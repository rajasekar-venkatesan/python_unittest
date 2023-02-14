# Part 1
# Introduction to Unit Testing in Python

## Software Testing

<br>

**Software testing** is a process of evaluating a software system or its component(s) with the intent to find whether it meets the specified requirements or not. It involves executing a software component or system to identify any gaps, errors, or missing requirements, and to evaluate its overall quality and performance.

<br>

In Data Science (DS) projects, software testing is extremely important as these projects typically involve processing vast amounts of data and making predictions based on that data. A software bug or error in these projects can result in incorrect predictions or decisions, which can have significant consequences.

<br>

Moreover, DS projects are complex and involve many components such as data pre-processing, feature selection, model training, and evaluation. Software testing helps to ensure that each component is functioning correctly, which in turn ensures that the overall system is functioning as expected.

<br>

Also, our team is the only development team in our organization that is not part of the standard CI/CD pipeline to deploy our code to production. Therefore, currently, we are responsible for manually testing our code ourselves.

<br>

## Python Unittest Module

<br>

The **unittest** module in Python is a built-in library for writing and running tests for your code. It provides a framework for writing automated tests that can be run repeatedly, making it easier to catch and fix bugs early in the development process.

<br>

Here are some of the key features of the unittest module in Python:

 - **Test Fixtures:** unittest supports the concept of test fixtures, which are resources that are set up before a test is run and torn down after the test has completed. This allows you to isolate the tests from each other and to avoid side-effects that can cause tests to fail.

 - **Test Discovery:** unittest provides a mechanism for discovering tests automatically, which makes it easier to run all the tests for a project without having to manually specify which tests should be run.

 - **Assertions:** unittest provides a rich set of assertions to check the behavior of your code. These assertions can be used to verify that your code behaves as expected, and to provide meaningful error messages when it doesn't.

 - **Test Suites:** unittest allows you to organize your tests into suites, which can be run as a group. This makes it easy to run a subset of tests or to run tests in a specific order.

 - **Test Reporting:** unittest provides a mechanism for reporting the results of tests, making it easy to see which tests passed and which failed.

 - **Mocking:** unittest provides support for mocking, which allows you to replace parts of your code with fake objects for testing purposes. This makes it easier to test complex systems by isolating the parts that you want to test.

<br>

In conclusion, the unittest module in Python is a powerful tool for writing automated tests for your code. Its features make it easy to write tests that are reliable, repeatable, and easy to maintain, which in turn helps you to catch and fix bugs early in the development process.

<br>

## Using the ```unittest``` module

<br>

Here is an example of how you can write basic unit tests using the unittest module in Python:

```
import unittest

def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

class TestMathFunctions(unittest.TestCase):
    def test_add(self):
        self.assertEqual(add(1, 2), 3)
        self.assertEqual(add(-1, -1), -2)
        self.assertEqual(add(0, 0), 0)
        
    def test_subtract(self):
        self.assertEqual(subtract(1, 2), -1)
        self.assertEqual(subtract(-1, -1), 0)
        self.assertEqual(subtract(0, 0), 0)

if __name__ == '__main__':
    unittest.main()
```

In this example, the ```TestMathFunctions``` class defines two test methods, ```test_add``` and ```test_subtract```, which test the add and subtract functions respectively. The ```assertEqual``` method is used to verify that the result of the function is equal to the expected value.

<br>

To run the tests, you can simply run the Python script. The unittest module will discover the tests automatically and run them for you, and will report the results of the tests. If any of the tests fail, the unittest module will print an error message indicating which test failed and why.

<br>

Note that this is just a simple example, and the unittest module provides many more features and options for writing and running tests. You can find more information in the Python documentation: https://docs.python.org/3/library/unittest.html

<br>

## Unittest Structure 

<br>

A **test case** is a single unit of testing, which tests a specific aspect of the code. A test case typically consists of a set of inputs and the expected output or behavior, and a method to verify that the code produces the expected result.

<br>

In the unittest module, test cases are defined as methods within a class that is derived from ```unittest.TestCase```. The methods that define the test cases should start with the word **test**, and should use the various assertions provided by the unittest module to verify the behavior of the code under test.

<br>

A **test suite** is a collection of test cases that are grouped together for a specific purpose. Test suites allow you to organize your tests into logical groups and to run a specific set of tests as needed. In the unittest module, test suites are created by defining multiple test cases within a single test case class, or by grouping multiple test case classes together.

<br>

Here is an example of how you can structure test cases and test suites using the unittest module:

```
import unittest

def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

class TestMathFunctions(unittest.TestCase):
    def test_add(self):
        self.assertEqual(add(1, 2), 3)
        self.assertEqual(add(-1, -1), -2)
        self.assertEqual(add(0, 0), 0)
        
    def test_subtract(self):
        self.assertEqual(subtract(1, 2), -1)
        self.assertEqual(subtract(-1, -1), 0)
        self.assertEqual(subtract(0, 0), 0)

class TestMathFunctionsAdvanced(unittest.TestCase):
    def test_add_advanced(self):
        self.assertEqual(add('a', 'b'), 'ab')
        self.assertEqual(add(-1.5, -1.5), -3)
        self.assertEqual(add(10, 2.0), 12.0)
    
    def test_subtract_advanced(self):
        self.assertEqual(subtract(1, 2.0), -1.0)
        self.assertEqual(subtract(-1, -1), 0)
        self.assertEqual(subtract(0, 0), 0)

if __name__ == '__main__':
    suite = unittest.TestSuite()
    suite.addTest(unittest.makeSuite(TestMathFunctions))
    suite.addTest(unittest.makeSuite(TestMathFunctionsAdvanced))
    unittest.TextTestRunner().run(suite)
```

<br>

In this example, there are two test case classes, ```TestMathFunctions``` and ```TestMathFunctionsAdvanced```, each with its own set of test cases. The test cases are added to a test suite using the ```addTest``` method, and the suite is then run using the run method of the unittest. ```TextTestRunner``` class. This allows you to run all the tests in a specific order, or to run a specific set of tests as needed.

<br>

## ```assert``` statements

<br>

The ```assert``` statement in Python is used to verify that a certain condition is true. If the condition is true, the assert statement does nothing. If the condition is false, the assert statement raises an ```AssertionError``` exception, which stops the execution of the program and provides an error message.

<br>

In the context of writing unit tests, the assert statement is used to verify that the code under test behaves as expected. For example, you might write a test to verify that a function returns the correct result, or that a certain condition is true after a certain operation is performed.

<br>

Here is an example of how you can use the assert statement in a unit test:

```
import unittest

def add(a, b):
    return a + b

class TestMathFunctions(unittest.TestCase):
    def test_add(self):
        result = add(1, 2)
        self.assertEqual(result, 3)

if __name__ == '__main__':
    unittest.main()
```

<br>

In this example, the ```test_add``` method calls the add function and stores the result in the result variable. The ```assertEqual``` method is then used to verify that the value of result is equal to 3, which is the expected result. If the value of result is not equal to 3, the ```assertEqual``` method will raise an ```AssertionError```, and the test will fail.

<br>

Note that the unittest module provides a number of assertion methods, including ```assertEqual, assertNotEqual, assertTrue, assertFalse, assertIs, assertIsNot``` and many others. These assertion methods provide a convenient way to verify the behavior of the code under test, and make it easy to write tests that are concise and easy to understand.

