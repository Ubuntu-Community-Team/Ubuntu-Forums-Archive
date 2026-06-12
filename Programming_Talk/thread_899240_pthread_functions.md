---
title: "pthread functions"
date: 2008-08-24
forum: Programming Talk
---

### Post by Ristar on 2008-08-24
hello, another pthread qn...


how do i make both threads have access to the same set of updated data, when they call different functions?

in addition, is the way i pass in the variable "myObjs" correct? can i pass in STL containers the same way?

example:

```

...

class aClass{
...
};

int main(){
    void *plus (void *);
    void *minus (void *);
    pthread_t thread1, thread2;
    ...
    queue<aClass> myObjs;
    ...
    int size = myObjs.size(); //this is OK.
    retVal1 = pthread_create(&thread1, NULL, plus, (void *) myObjs);
    retVal2 = pthread_create(&thread2, NULL, minus, (void *) myObjs);
    ...
}
...

void *plus(void *ptr){
    queue<aClass> *myObjs = (vector<aClass>*) *ptr;
    [COLOR="Red"]int size = myObjs.size(); //generates error. how do i resolve this?[/COLOR]
}

```

in this code, thread1 will increase the value of member variables, while thread2 will decrease the value of the member variables... but i need them to be updated.

in addition, when im adding the values, how do i mutex lock the minus function, so it wont add and minus at the same time, and vice versa?

if i change the code to use STL container, i would edit the function "plus()" to add a new object, and the function "minus()" to erase an object.

lastly, how do i use the functions in queue, and the class? it generates an error when it's in the thread function.

the error is:
[COLOR="Red"]error: request for member 'size' in 'myObjs', which is non class type 'std::queue<aClass, std:: deque<aClass, std::allocator <aClass>>>*'[/COLOR]

---

### Post by Ristar on 2008-08-24
> **Ristar said:**
> 

```

...
void *plus(void *ptr){
    queue<aClass> *myObjs = (vector<aClass>*) *ptr;
    [COLOR="Red"]int size = myObjs.size(); //generates error. how do i resolve this?[/COLOR]
}

```

the error is:
[COLOR="Red"]error: request for member 'size' in 'myObjs', which is non class type 'std::queue<aClass, std:: deque<aClass, std::allocator <aClass>>>*'[/COLOR]

error has been resolved by using the 'arrow'

so, can anyone help with the original questions?

thanks.

---

### Post by dribeas on 2008-08-24
> **Ristar said:**
> 
how do i make both threads have access to the same set of updated data, when they call different functions?

in addition, is the way i pass in the variable "myObjs" correct? can i pass in STL containers the same way?


For the second question, passing an STL container as you did above is correct. After instantiation a templated class is just like any other regular class.

Then, for the first question: how can you **not** have access to the same data? Your problem will be that STL containers are not thread safe, so that you'll need to provide some kind of mutual exclusion to guarantee correct data. Note that the problem is not getting obsolete data, but getting data in the middle of an update: one thread is updating the container, but as some member fields/contained elements are in the middle of an update the second thread may try to read, getting part of the unchanged state and part of the changed state.

I would try to encapsulate the container together with the synchronization elements (mutex) in a class. Any operation in the class would acquire the mutex and then call the appropriate operation on the container, releasing the mutex afterwards (through RAII). Also consider using some higher level threading library if you are going to code in C++, first recommendation would be boost, but there are others (ACE, poco, QT, wxWidgets...)

   David

---

