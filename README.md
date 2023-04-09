# Assignment-Exceptions
This program demonstrates four different exceptions:  runtime_error, domain_error, and out_of_range.  It also uses different catch types and includes a good user experience with an explanation  of the program at the beginning.
/* Sanyerlis Camacaro- CSC275 - Sancamac@uat.edu Assignment: Exceptions
This code demonstrates how to:
Write a program that demonstrates the try/catch exception handler blocks 
for a minimum of 2 different exceptions. Use more than one catch type.  
In addition, include at least 1 exception handling that doesn't use try/catch.   
Include sufficient output to indicate the exception and the condition that caused it.

Expectations
Display a description of the program and how to use it for the user when it the application starts.
Over comment your code!
The program should do something in addition to demonstrate exceptions.
This program should have a good UX. 

This program demonstrates four different exceptions: 
runtime_error, domain_error, and out_of_range. 
It also uses different catch types and includes a good user experience with an explanation 
of the program at the beginning.
*/

#include <iostream> // includes input and out as the standard library.
#include <stdexcept> // it defines the classes that the C++ Standard Library itself and C++ programs may use to report certain errors.
#include <cmath> // declares a set of functions to compute common mathematical operations and transformations.
#include <vector> // telling the compiler to not only use your own code, but to also compile a file called vector.


using namespace std; // means using standard namespace and that I dont have to type std:: in front of each line.


// Function to perform division operation.

double divide(double a, double b) {

    if (b == 0) {

        throw runtime_error("Division by zero");

    }

    return a / b;

}



// Function to perform square root operation.

double squareRoot(double number) {

    if (number < 0) {

        throw domain_error("Square root of a negative number");

    }

    return sqrt(number);

}



// Function to access an element in a vector.

int getElement(const vector<int>& v, int index) {

    if (index < 0 || index >= static_cast<int>(v.size())) {

        throw out_of_range("Index out of range");

    }

    return v[index];

}



int main() {

    cout << "\nWelcome to the Exception Handling Demo Program!\n" << endl;

    cout << "\nThis program demonstrates different exception handling techniques while performing some operations.\n" << endl;

    cout << "\nThe operations are: Division, Square Root, and Accessing an Array Element.\n" << endl << endl;



    while (true) {

        double a, b;

        cout << "Enter two numbers for division (a/b): ";

        cin >> a >> b;



        try {

            cout << "Result: " << divide(a, b) << endl;

        }
        catch (const runtime_error& e) {

            cerr << "Caught exception: " << e.what() << endl;

        }



        double number;

        cout << "Enter a number for square root: ";

        cin >> number;



        try {

            cout << "Square root: " << squareRoot(number) << endl;

        }
        catch (const domain_error& e) {

            cerr << "Caught exception: " << e.what() << endl;

        }



        vector<int> array = { 1, 2, 3, 4, 5 };

        int index;

        cout << "Enter an index to access the element in the array: ";

        cin >> index;



        try {

            cout << "Element at index " << index << ": " << getElement(array, index) << endl;

        }
        catch (const out_of_range& e) {

            cerr << "Caught exception: " << e.what() << endl;

        }



        char choice;

        cout << "Do you want to continue? (y/n): ";

        cin >> choice;

        if (choice == 'n' || choice == 'N') {

            break;

        }

        cout << endl;

    }



    cout << "Thank you for using the Exception Handling Demo Program!" << endl;



    return 0;

}

