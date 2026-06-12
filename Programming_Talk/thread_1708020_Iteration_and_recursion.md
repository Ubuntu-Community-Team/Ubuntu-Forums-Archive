---
title: "Iteration and recursion"
date: 2011-03-16
forum: Programming Talk
---

### Post by erotavlas on 2011-03-16
Hi,

I have to write a code with a iteration paradigm or with a recursion paradigm. I think that the first one is the best for performance even if it require more lines of code. But I don't know if I'm able to write a code that uses it.

I have to scan a vector of variables and I have to do a loop for every variable. I know the dimension of the vector, the problem is that the loops must be nested. How can I do it?

For instance
> 
vector variables [x, y,z]
for (x)
  for (y)
    for(z)



---

### Post by PaulM1985 on 2011-03-16
Based on your initial explanation I would say nested for-loops would be the way to go.  Have you any more information on what you are looking for in your 3-dimensional array or what you are trying to do?

If you need to access all elements, then nested for-loops would be as quick a way as any.

Paul

---

### Post by erotavlas on 2011-03-16
> **PaulM1985 said:**
> Based on your initial explanation I would say nested for-loops would be the way to go.  Have you any more information on what you are looking for in your 3-dimensional array or what you are trying to do?

If you need to access all elements, then nested for-loops would be as quick a way as any.

Paul

Ok. The vector of the variables can have different dimension. So I don't  know how many loop I have to do. I must read the vector and create a  loop on the fly and the loop must be nested.
Do you have any suggestions?

---

### Post by Arndt on 2011-03-16
> **erotavlas said:**
> Ok. The vector of the variables can have different dimension. So I don't  know how many loop I have to do. I must read the vector and create a  loop on the fly and the loop must be nested.
Do you have any suggestions?

What language are you to write this in?

---

### Post by erotavlas on 2011-03-16
> **arndt said:**
> what language are you to write this in?

c++

---

### Post by Some Penguin on 2011-03-16
> 
I know the dimension of the vector


> 
The vector of the variables can have different dimension. So I don't know how many loop I have to do.



You're being very unclear on whether you do or do not know the dimensions of the vector...

---

### Post by Arndt on 2011-03-16
> **erotavlas said:**
> Ok. The vector of the variables can have different dimension. So I don't  know how many loop I have to do. I must read the vector and create a  loop on the fly and the loop must be nested.
Do you have any suggestions?

Let's assume the vector has three elements. Can you show us pseudo code which describes exactly what should happen?

(Once you have done that, I'm going to ask you to do the same thing for a vector of four elements.)

---

### Post by erotavlas on 2011-03-16
> **Some Penguin said:**
> You're being very unclear on whether you do or do not know the dimensions of the vector...

I'm sorry. I have a vector of variables and so I know its dimension. For every variable I have to do a loop. Each loop must be nested inside the previous one.

```
(vector [x,y,z] ->
for(x) {
    for (y) {
        for (z) { }
    }
})
```

I have to create the loop on the fly because I don't know the dimension of the vector at compile time i.e. the vector can have different dimension. 
I hope that now the explanation is more clear.

---

### Post by PaulM1985 on 2011-03-16
Just to make this 100% clear, what are X, Y and Z in your example?

ints, floats, doubles, arrays?  You seem to be implying arrays but when you write vector[x, y, z] it makes me think of a 3d vector (eg a direction in 3d space) rather than a 3 dimensional array.

If these are 3 dimensional arrays, you could have nested std::vectors.  Using these you would be able to determine how many elements are in the vector using the size() function.   ([http://www.cplusplus.com/reference/stl/vector/](http://www.cplusplus.com/reference/stl/vector/))

Paul

---

### Post by erotavlas on 2011-03-16
> **PaulM1985 said:**
> Just to make this 100% clear, what are X, Y and Z in your example?

ints, floats, doubles, arrays?  You seem to be implying arrays but when you write vector[x, y, z] it makes me think of a 3d vector (eg a direction in 3d space) rather than a 3 dimensional array.

If these are 3 dimensional arrays, you could have nested std::vectors.  Using these you would be able to determine how many elements are in the vector using the size() function.   ([http://www.cplusplus.com/reference/stl/vector/](http://www.cplusplus.com/reference/stl/vector/))

Paul

The problem is a little bit more complicated...for each variable inside the vector I have to search inside an other memory structure. You can imagine each variable like a huge matrix (the matrix is the same).
For this purpose I have to do a nested loop...
Yes I know the STL library.

---

### Post by erotavlas on 2011-03-16
I'm sorry if my explanation is not good enough. I have to make an arbitrary number of nested loops. I would like to know if the only way is the recursion paradigm.

---

### Post by Arndt on 2011-03-16
> **erotavlas said:**
> I'm sorry if my explanation is not good enough. I have to make an arbitrary number of nested loops. I would like to know if the only way is the recursion paradigm.

No, but you need somewhere to store information about which combinations you have already encountered. The runtime stack (recursion) is one possibility, a home-made stack is another. There are other ways as well - you don't need to see the state as a stack.

---

### Post by erotavlas on 2011-04-01
In the last two weeks I have thought a lot about the my problem. This is my code with some adjustments

```

void Recurse(const vector<string>& variablesVector, Data* data)
{
    // terminate recursion
    if (variablesVector.size() == 0)
    {
        // do some operations with the data

        return;
    }

    // loop for the variable in the data    
    for (Data::const_iterator it = data->begin(); it != data->end(); ++it)
    {
         
    // recursive step - remove the front variable for the next iteration
        Recurse(variablesVector.erase(variablesVector.begin(), variablesVector.begin()+1), &data);
    }
}

```My code does the following operations. Given the vector of the variables and the Data (domain of the variables), it takes the first variable, search inside the domain of values Data and executes the recursive step. Takes the second variable, search inside the domain of values Data and executes the recursive step and so on.
At last step when there are no any variable in the vector, the code executes some operations on the data (each data for each variable).
I think that it realizes the behaviour of nested loops. 
```

Example:
For x For y For z -> variablesVector[x,y,z]
Domain for each variable -> Data
for x in subset(Data)
   for y in subset(Data)
      for z in subset (Data)
        do (x,y,z)

```Now I know that the complexity can be intractable with only small number of variables and small number of different values for each variable.
You are right, I can't use the template version if I don't know at compile time the number of variables in the vector ([http://www.codeguru.com/cpp/cpp/algorithms/math/print.php/c15111/](http://www.codeguru.com/cpp/cpp/algorithms/math/print.php/c15111/)). My vector is read from a parser, and so I don't know it before run time. Do you have a suggestions about how can I do to reduce the complexity of huge number of recursive calls?

---

### Post by erotavlas on 2011-04-04
For completeness, I post my formulation of the original problem. 

The problem is to evaluate a mathematical expression like "For  each x, For each y ... For each z F(x,y,...,z)" where x,y,...,z are the  variables while the F(x,y,...,z) is the function. 
I know only at run time the number of variables because the expression  is read from file. So I must do a recursive function, there is no  another way.
I would like to know how can I get the best performance from my code, for this purpose I have posted a question in this forum.

---

### Post by Arndt on 2011-04-04
> **erotavlas said:**
> For completeness, I post my formulation of the original problem. 

The problem is to evaluate a mathematical expression like "For  each x, For each y ... For each z F(x,y,...,z)" where x,y,...,z are the  variables while the F(x,y,...,z) is the function. 
I know only at run time the number of variables because the expression  is read from file. So I must do a recursive function, there is no  another way.
I would like to know how can I get the best performance from my code, for this purpose I have posted a question in this forum.

If you have, say, five variables, and they can each take on values from 1 to 1000, then you will have to make 10^15 calls to F, regardless of whether you implement it recursively or not. Do you know something about the function that could let you skip certain combinations? If not, I don't see how you can get around making that many calls.

How do you execute F? I hope you don't reparse it from its text representation each time, but precompile it somehow.

---

