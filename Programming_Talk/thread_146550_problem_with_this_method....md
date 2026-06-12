---
title: "problem with this method..."
date: 2006-03-18
forum: Programming Talk
---

### Post by ImplicitProcrastination on 2006-03-18
Hi y'all, I was wondering if you would be willing to help me with my homework.

I'm learning how to work with lists recursively and I'm writing a method that automatically sorts a list. It seems to only be adding null as opposed to my object. 

I'm allowed to seek help to get pointed in the right direction, or you can even tell me what corrections to make if it's not that easy but the main thing is I have to come to an understanding of it. In trying to run SortedRecursiveList I suspect there is a problem with my add method in SortedRecursiveList, I did some tracing and figured maybe it's because the part of it that determines if it's empty is always seeing rest.first and thus spitting null, thus the this.first, but that doesn't seem to be the problem and I'm really in the hole on my CS and have been spending alot (too much for midterm season) of time on this.

This is on an honor code so you don't have to worry about whether this is helping me cheat or not, I'd really appreciate an in depth explanation. I'll forward this to my professor if you want.

RecursiveList.java:

```


import java.util.*;

public class RecursiveList extends AbstractList
{
    Object first;
    RecursiveList rest;

    RecursiveList() {        
	//  initializes an empty list
	first = rest = null;
    }

    RecursiveList(Object item){        
	//  initializes a list with one element
    
	first = item;
	rest = new RecursiveList();

    }

    RecursiveList(Object item, RecursiveList rest){  
	//  initializes a list with a given 
	//first element and rest-of list

	first = item;
	this.rest = rest;
    }

    protected void prepend(Object item){
	rest = new RecursiveList(first,rest);
	first = item;
    }

    protected Object removeFirst(){
	if(isEmpty())
	    return null;
	else {
	    Object temp = first;
	    first = rest.first;
	    rest = rest.rest;
	    return temp;
	}
    }

    public Object getFirst(){
	return first;
    }

    public RecursiveList getRest(){
	return rest;
    }

    public void clear(){
	first = rest = null;
    }

    public boolean isEmpty(){

	return rest==null;
    }

    public int size(){
	if(isEmpty())
	    return 0;
	else
	    return 1+rest.size();
    }

    public boolean add(Object item)
    {
	if(isEmpty())
	    prepend(item);
    
	else
	    rest.add(item);
	return true;
    }

    public Object get(int index)
    {
	Object result;

	if(isEmpty())
	    throw new IndexOutOfBoundsException();
	else if(index==0)
	    result = first;
	else
	    result = rest.get(index-1);
	return result;
    }

    public Object set(int index, Object obj)
    {
	Object result;

	if(isEmpty())
	    throw new IndexOutOfBoundsException();
	else if(index==0){
	    result = first;
	    first = obj;
	}
	else
	    result = rest.set(index-1, obj);

	return result;
    }

    public Object remove(int index)
    {
	Object result;
	if(isEmpty() || index<0)
	    throw new IndexOutOfBoundsException();
	else if(index==0)
	    result = removeFirst();
	else
	    result = rest.remove(index-1);
	return result;
    }

    public void add(int index, Object item)
    {
	if(index==0)
	    prepend(item);
	else if (isEmpty() || index<0)
	    throw new IndexOutOfBoundsException();
	else
	    rest.add(index - 1, item);
    }




    public int indexOf(Object item){  
	//  Search for obj in this list.  
	//If it is found, return the index of the 
	//position of its first occurrence; 
	//otherwise return -1.
    

	if(isEmpty()){
	    return -1;
	}

	else{
	    if(first.equals(item)){
		return 0;
	    }
	    else{
		int pos = 1 + rest.indexOf(item);
		if(pos == -1){
		    return -1;
		}
		else{
		    return rest.indexOf(item) + 1;
		}
	    }
	}
    }

    public boolean remove(Object item){
	//Search for obj in this list. 
	//If it is found, delete it 
	//(that is, its first occurrence) and return true; 
	//otherwise return false

	if(isEmpty()){
	    throw new IndexOutOfBoundsException();
	}
	else{
	    if(first.equals(item)){
		remove(indexOf(item));
		return true;
	    }
	    else{
	    
		rest.remove(item);
	    }   
	    return false;
	}
    }


    public static void main(String args[]){
	RecursiveList newList = new RecursiveList();

	newList.add(0,"ian");
	newList.add(1,"p");
	newList.add(2,"shuley");
    
	System.out.println(newList.indexOf("ian"));
	System.out.println(newList.indexOf("shuley"));//tests indexOf() call

	System.out.println(newList);

	newList.remove("p");

	System.out.println(newList);
    }
}

```

SortedRecursiveList.java:

```

import java.util.*;

public class SortedRecursiveList extends RecursiveList
{

    Object first;
    SortedRecursiveList rest;

    SortedRecursiveList(){
	//initialize empty list
	first = rest = null;
    }

    SortedRecursiveList(Object item){
	first = item;
	rest = new SortedRecursiveList();
    }

    SortedRecursiveList(Object item, SortedRecursiveList rest){
	first = item;
	this.rest = rest;
    }

    public void add(int index, Object item){
	throwOne();

    }

    public Object set(int index, Object item){
	throwOne();
	return null;
    }

    void throwOne() throws UnsupportedOperationException{ 
	
	throw new IndexOutOfBoundsException();
    }

    protected void prepend(Object item){
	rest = new SortedRecursiveList(first, rest);
	first = item;
    }


    public boolean add(Object item)
    {
	if(this.first == null){
	    rest = new SortedRecursiveList();
	    first = item;
	    return true;
	}

	String item1 = item.toString();
	String first1 = first.toString();

	if(first1.compareTo(item1) < 0) {
	    rest.add(item);
	    //return true;
	}

	if(first1.compareTo(item1) >= 0){
	    prepend(item);
	    return true;
	}

	return false;
    }

    public int indexOf(Object item){
	String num1 = first.toString();
	String item1 = item.toString();
	
	if(isEmpty()){
	    return -1;
	}

	if(num1.compareTo(item1) == 0)
	    return 1 + rest.indexOf(item);
	
	if(num1.compareTo(item1) <  0)
	    rest.indexOf(item);
		
	return -1;
    }

    public boolean remove(Object item){
	
	String num1 = first.toString();
	String item1 = item.toString();

	if(isEmpty()){
	    throw new IndexOutOfBoundsException();
	}
	else{
	    if(num1.compareTo(item1) == 0){
		remove(indexOf(item));
		return true;
	    }
	    if(num1.compareTo(item1) < 0){
		rest.remove(item);
		return false;
	    }
	    	       
	    return false;
	}
    }

    public static void main(String[] args){
	SortedRecursiveList testList = new SortedRecursiveList();

	testList.add("shuley");
	System.out.println(testList);
	testList.add("zebra");
	testList.add("98673");
	testList.add("test");

	System.out.println(testList.indexOf("test"));
	//System.out.println(testList.first);
	System.out.println(testList.indexOf("shuley"));
	System.out.println(testList.indexOf("zebra"));
	System.out.println(testList.indexOf("98673"));

    }

}


```

Much Thanks.

---

### Post by thumper on 2006-03-19
Take another look at this and decide if it is really what you want.  Hint: I don't think it is :)
```

    public boolean isEmpty(){

	return rest==null;
    }

```

---

### Post by ImplicitProcrastination on 2006-03-19
Apparently I'm not supposed to be comparing the string but comparing the objects directly.


I'm just so befuddled about how to do that without converting them to Strings. Yea, theres the Comparator interface but is it possible to extend something and implement something at the same time?

To catch you up to speed further a quick google for RecursiveList SortedRecursiveList and the first result is the lab I'm working on.

I tried changing it return first==null; and it still is throwing null.

---

### Post by Roptaty on 2006-03-20
Why are you declaring first and rest in both classes? You have now TWO variables of both first and rest... You have RecursiveList.{first|rest} and SortedRecursiveList.{first|rest}. Methods in RecursiveList will use RecursiveList's copies, while methods in Sorted will use its instances of the variables. 


If your classes should only deal with strings, I strongly suggest that you use String instead of Object in your classes.

---

