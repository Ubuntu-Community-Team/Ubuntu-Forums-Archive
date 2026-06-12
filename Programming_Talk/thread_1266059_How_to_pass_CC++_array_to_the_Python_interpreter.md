---
title: "How to pass C/C++ array to the Python interpreter?"
date: 2009-09-14
forum: Programming Talk
---

### Post by c174 on 2009-09-14
I want to extend my application with Python scripts. My application reads numeric data from files and stores it as matrices. From those matrices I can extract a single column vector, and given two of those I can plot a curve.

It would be nice to do operations on the matrices and/or vectors before plotting the result. That is, the user should be able to enter these operations directly in a text field (the application has a graphical user-interface). I think the Python interpreter would be very handy, so that I don't need to write my own expression parser. Unfortunately, I have some trouble figuring out how to convert a C/C++ array to a Python object...

I have this so far

C++ file: main.cpp
```
#include <iostream>
#include "Python.h"


int main( int argc, char* argv[] )
{
   double answer = 0;
   PyObject *modname, *mod, *mdict, *func, *expr, *val1, *val2, *vars, *args, *rslt;
         
   // launch the python interpreter
   Py_Initialize();
	
   // load file "Test.py"
   modname = PyString_FromString("Test");
   mod = PyImport_Import(modname);
	if (mod) 
	{
	   // get a dictionary of function available in the module
           mdict = PyModule_GetDict(mod);
		
	   // grab one specific function called "interpret"
           func = PyDict_GetItemString(mdict, "interpret");
	   if (func) 
	   {
		if (PyCallable_Check(func)) 
		{
		   // define a python script
		   expr = PyString_FromString("x+y");
				
		   // define the variables used in the script above
		   //
		   // In this example I used doubles, which is easy. But I would like to be
		   // able to define python objects from arrays also, for example
		   //
		   //    double* a = new double[100]; // a vector
		   //
		   // or 
		   //    
		   //    double** m = new double*[4];
		   //    m[0] = new double[4*3];
		   //    m[1] = m[0] + 3;
		   //    m[2] = m[1] + 3;
		   //    m[3] = m[2] + 3; // a 4-by-3 matrix
		   //
		   // how to convert "a" and "m" to python objects?			
		   val1 = PyFloat_FromDouble(5.0);
		   val2 = PyFloat_FromDouble(4.0);
		   vars = PyDict_New();
		   PyDict_SetItemString( vars, "x", val1 );
		   PyDict_SetItemString( vars, "y", val2 );
				
		   // create arguments for the python function
		   args = PyTuple_New(2);
		   PyTuple_SetItem(args, 0, expr);
		   PyTuple_SetItem(args, 1, vars);
				
		   // call the python interpreter
		   rslt = PyObject_CallObject(func, args);
		   if (rslt) 
		   {
		      // convert from python to c
		      answer = PyFloat_AsDouble(rslt);
		      Py_XDECREF(rslt);
		   }
                   Py_XDECREF(expr);
                   Py_XDECREF(val1);
                   Py_XDECREF(val2);
                   Py_XDECREF(vars);
                   Py_XDECREF(args);
		}
	    }
            Py_XDECREF(mod);
	}
         
	Py_XDECREF(modname);
         
	Py_Finalize();

        // print result in terminal
	printf("%g",answer);
	getchar();

   return 0;
}
```

Python file: Test.py
```
def interpret( expr, vars ):
    return eval( expr, {}, vars );
```

I searched the web for a while, but I didn't find an example that shows just the case I'm interested in. I have read about Buffer Objects in the Python/C API, but unfortunately there is no example code and the text is too condensed for my level:confused:

---

### Post by c174 on 2009-09-16
Okay, I managed to figure it out myself: 

1) Use package NumPy to represent matrices (N-dimensional) in Python
2) Read some of the NumPy C API -- it is quite similar to the Python/C API
3) Be careful about reference counting (e.g. borrowing and stealing references) - hope I did it right :)
4) Handle exceptions from parsing/running the Python script

Below is a test code based on the points above. It implements an interface between C++ and Python, so that you can execute either a single statement or a complete Python script. Variables are communicated from C++ to Python and back again. I hope this will be useful for others.

In the code I have used classic C-style vectors and arrays but that can of course be replaced by STL vector or other containers, as long as the data buffer can be accessed.

Boost.Python has some stuff for calling C++ from Python, but the other way around (which is the topic here) is not very far yet.

File: main.cpp
```
#include "Python.h"
#include "C:\Python26\Lib\site-packages\numpy\core\include\numpy\arrayobject.h"

void output_result( PyObject* rslt )
{
   if( !rslt ) {
      printf("output_result: argument must be a valid pointer\n");
      return;
   } 
	
   // output scalar result
   if( PyFloat_Check(rslt) ) {
      printf( "result: %f\n", PyFloat_AsDouble(rslt) );
   }
   
   if( PyArray_Check(rslt) ) {
      PyArrayObject* obj = PyArray_GETCONTIGUOUS( (PyArrayObject*) rslt );  
      int ndims = obj->nd;
      int* dims = obj->dimensions; // not copying data   
      double* data = (double*) obj->data; // not copying data
      int i, j, k = 0;
      
      // output vector result
      if( ndims == 1 ) {
         for( i=0; i<dims[0]; i++ )
            printf( "element: %i  value: %f\n", i, data[k++] );
         printf("\n");
      }
      
      // output matrix reult
      else if( ndims == 2 ) {
         for( i=0; i<dims[0]; i++ ) {
            for( j=0; j<dims[1]; j++ )
               printf( "%f  ", data[k++] );		
            printf( "\n" );  
         }            
      }
      
      // output N-D result
      else {
         for( i=0; i<ndims; i++ )
            for( j=0; j<dims[i]; j++ )
               printf( "dimension: %i  element: %i  value: %f\n", i, j, data[k++] );		
      }		         
      
      // clean
      Py_XDECREF(obj);
   }				   
}

void handle_error( PyObject* fe )
{
   // get exception info
   PyObject *type, *value, *traceback;
   PyErr_Fetch( &type, &value, &traceback );
   PyErr_NormalizeException( &type, &value, &traceback );
   
   // create a argument for "format exception"
   PyObject* args = PyTuple_New(3);
   PyTuple_SetItem( args, 0, type );
   PyTuple_SetItem( args, 1, value );
   PyTuple_SetItem( args, 2, traceback );
   
   // get a list of string describing what went wrong
   PyObject* output = PyObject_CallObject( fe, args );
   
   // print error message
   int i, n = PyList_Size( output );
   for( i=0; i<n; i++ ) printf( "%s", PyString_AsString( PyList_GetItem( output, i ) ) );		
   
   // clean up
   Py_XDECREF( args );
   Py_XDECREF( output );
}	

			
int main( int argc, char* argv[] )
{
   PyObject *mod1, *mod2, *dict1, *dict2, *func1, *func2, *fexcp, 
            *expr, *script, 
            *scalar1, *scalar2, *vec, *mat, 
            *vars, *args1, *args2, *rslt1, *rslt2, *rslt3;

   // launch the python interpreter
   Py_Initialize();

   // this macro is defined be NumPy and must be included
   import_array1(-1);   	

   // load module "traceback" (for error handling) and module from file "Test.py"
   mod1 = PyImport_ImportModule( "traceback" );
   mod2 = PyImport_ImportModule( "Test" );
   if( mod1 && mod2 ) 
   {
      // get dictionary of available items in the modules
      dict1 = PyModule_GetDict(mod1);
      dict2 = PyModule_GetDict(mod2);

      // grab the functions we are interested in
      fexcp = PyDict_GetItemString(dict1, "format_exception");
      func1 = PyDict_GetItemString(dict2, "run_expression");
      func2 = PyDict_GetItemString(dict2, "run_script");            
      if( func1 && func2 && fexcp ) 
      {
         if( PyCallable_Check(func1) && PyCallable_Check(func2) && PyCallable_Check(fexcp) ) 
         {
            // define a python expression and a python script
            expr = PyString_FromString("m[0:3,0]");
            script = PyString_FromString( "import numpy\n"				                            
                                          "def myfunction( a ):\n"
                                          "   '''do something'''\n"				                             
                                          "   return a[:,0]\n"
                                          "\n"
                                          "M = numpy.array( [[ 1, 2, 3 ], [ 4, 5, 6 ]], float )\n"
                                          "value = myfunction( M )\n"  				                             
                                          "print M\n"
                                          "print_fsdf value\n" );				                             

            // define some scalars
            scalar1 = PyFloat_FromDouble(5.0);
            scalar2 = PyFloat_FromDouble(4.0);

            // define a vector
            double* v = new double[3];
            v[0] = 1.0;
            v[1] = 2.0;
            v[2] = 3.0;				
            int vdim[] = { 3 };
            vec = PyArray_SimpleNewFromData( 1, vdim, PyArray_DOUBLE, v );

            // define a matrix using the classical C-format:
            // pointer-to-pointer-to-numeric type, last dimension running fastest
            //			
            // setup pointers
            const int nrow = 3, ncol = 4, nelem = nrow*ncol;
            double** m = new double*[nrow];
            m[0] = new double[nelem];
            m[1] = m[0] + ncol;
            m[2] = m[1] + ncol;				
            //
            // fill in values				
            m[0][0] = 1.0; m[0][1] = 2.0; m[0][2] = 5.0; m[0][3] = 34;
            m[1][0] = 5.0; m[1][1] = 1.0; m[1][2] = 8.0; m[1][3] = 64;
            m[2][0] = 8.0; m[2][1] = 0.0; m[2][2] = 3.0; m[2][3] = 12;
            int mdim[] = { nrow, ncol };
            mat = PyArray_SimpleNewFromData( 2, mdim, PyArray_DOUBLE, m[0] );

            // put variables into dictionary of local variables for python
            vars = PyDict_New();
            PyDict_SetItemString( vars, "x", scalar1 );
            PyDict_SetItemString( vars, "y", scalar2 );
            PyDict_SetItemString( vars, "v", vec );
            PyDict_SetItemString( vars, "m", mat );

            // create arguments for "run_expression"
            args1 = PyTuple_New(2);
            PyTuple_SetItem(args1, 0, expr);
            PyTuple_SetItem(args1, 1, vars);

            // create argument for "run_script"
            Py_INCREF(vars);
            args2 = PyTuple_New(2);
            PyTuple_SetItem(args2, 0, script);
            PyTuple_SetItem(args2, 1, vars);

            // execute single expression
            rslt1 = PyObject_CallObject(func1, args1);
            if( !rslt1 ) 
               handle_error( fexcp );
            else         
               output_result( rslt1 );  
            Py_XDECREF(rslt1);

            // execute script
            rslt2 = PyObject_CallObject(func2, args2);
            if( !rslt2 ) 
               handle_error( fexcp );				   
            else {
               rslt3 = PyDict_GetItemString( rslt2, "value" );
               if( !rslt3 ) 
                  printf( "Requested variable not defined during evaluation of script\n" );
               else        
                  output_result( rslt3 );
               Py_XDECREF(rslt3);
            }
            Py_XDECREF(rslt2);

            //
            Py_XDECREF(args1); // also decrements expr and vars
            Py_XDECREF(args2); // also decrements script and vars
            Py_XDECREF(mat);
            delete[] m[0];
            delete[] m;
            Py_XDECREF(vec);
            delete[] v;            
            Py_XDECREF(scalar2);
            Py_XDECREF(scalar1);                  
            Py_XDECREF(script);
            Py_XDECREF(expr);
         }
      }         
      Py_XDECREF(func1);
      Py_XDECREF(func2);
      Py_XDECREF(fexcp);				
   }         
   Py_XDECREF(mod1);
   Py_XDECREF(mod2);

   // (to keep debug console open on windows)
   getchar();         

   Py_Finalize();

   return 0;
}
```


File: Test.py
```
def run_expression( expr, vars ):
    return eval( expr, {}, vars )
    
def run_script( expr, vars ):    
    exec( expr, {}, vars );
    return locals()['vars']
   
```

---

