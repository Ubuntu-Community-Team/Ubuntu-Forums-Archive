---
title: "[Java] issue with a heap sort"
date: 2009-02-12
forum: Programming Talk
---

### Post by shadylookin on 2009-02-12
I'm trying to write a program that takes user input and uses a heap sort algorithm to sort integers. Thus far my program takes the user input and once you hit enter it apparently goes into an infinite loop(but I can't tell where). Oddly when I hit terminate in eclipse there's about a 50% chance that the correct answer will be output, but only after I click terminate. 

[PHP]import java.util.Scanner;

public class Driver {

	public static void main(String args[]){
		Heap heap = new Heap();
		System.out.print("enter you integers to be heap sorted: ");
		Scanner input = new Scanner(System.in);
		while(input.hasNextInt()){
			heap.add(input.nextInt());
		}	
		input.close();
		System.out.print("\nsorted integers: ");
		while(heap.getSize() > 0){
			int number = heap.removeFromHeap();
			System.out.print(number+" ");
		}
		
	}
	
}
[/PHP]

[PHP]import java.util.ArrayList;

public class Heap {

	private ArrayList<Integer> array = new ArrayList<Integer>();
	private int size = 0;

	/**
	 * used to initially build the heap
	 * @param newInt
	 * an integer to be added to the heap
	 */
	public void add(int newInt){
		size++;
		int newIndex = size -1;
		array.add(newInt);
		while(true){
			int parentIndex = ((newIndex -1) /2);
			if(array.get(newIndex) < array.get(parentIndex)){
				swap(newIndex, parentIndex);
				newIndex = parentIndex;
			} else{
				break;
			}
		}
		
	}
	
	/**
	 * swaps the numbers at the specified indices 
	 * @param firstIndex
	 * the first index
	 * @param secondIndex
	 * the second index
	 */
	public void swap(int firstIndex, int secondIndex){
		int swap = array.get(firstIndex);
		array.set(firstIndex, array.get(secondIndex));
		array.set(secondIndex, swap);
	}
	
	/**
	 * 
	 * @return
	 * the amount of numbers in the arraylist
	 */
	public int getSize() {
		return size;
	}

	/**
	 * used to rebuild the heap after a number has been pulled off the
	 * top
	 */
	public void rebuildHeap() {
		for(int index = 0; index <= ((size - 2) / 2); index++) {
			//System.out.println("in loop\n");
			int smallestChildIndex = index;
			if ((index * 2 + 1) <= (size-1) && (index * 2 + 2) <= (size-1)) {
				if (array.get(index * 2 + 1) < array.get(index * 2 + 2)) {
					smallestChildIndex = index * 2 + 1;
				} else {
					smallestChildIndex = index * 2 + 2;
				}
				if (array.get(smallestChildIndex) < array.get(index)) {
					swap(index, smallestChildIndex);
				}
			} else if ((index * 2 + 1) <= (size-1)) {
				smallestChildIndex = index * 2 + 1;
				if (array.get(smallestChildIndex) < array.get(index)) {
					swap(index, smallestChildIndex);
				}
			} 
		}
		//System.out.print("out of loop\n");
	}
	
	/**
	 * 
	 * @return
	 * the smallest element(top element) on the heap 
	 */
	public int removeFromHeap(){
		int topValue = array.get(0);
		array.set(0, array.get(size-1));
		array.remove(size-1);
		size--;
		rebuildHeap();
		return topValue;
	}

}
[/PHP]

there's my code if it helps. I'm puzzled as to what is going on and hope an extra pair of eyes can see what I've done wrong.

---

### Post by kavon89 on 2009-02-12
I think there is a problem with your add method.

```

size++; 
int newIndex = size - 1; 
int parentIndex = ((newIndex -1) /2); 
```

if newIndex <= 2, then parentIndex == 0 because -0.5, 0, and 0.5 are all truncated to 0 because it is an int. I'm not sure if this is intended but it seemed very odd when I looked at it. This will also happen when newIndex is any even number greater than 2, 3/2 is truncated to 1 etc.

---

### Post by shadylookin on 2009-02-12
> **kavon89 said:**
> I think there is a problem with your add method.

```

size++; 
int newIndex = size - 1; 
int parentIndex = ((newIndex -1) /2); 
```

if newIndex <= 2, then parentIndex == 0 because -0.5, 0, and 0.5 are all truncated to 0 because it is an int. I'm not sure if this is intended but it seemed very odd when I looked at it. This will also happen when newIndex is any even number greater than 2, 3/2 is truncated to 1 etc.

well arrays in java start at 0. there's nothing before 0 so index 0 is it's own parent. index 1 is the left child of index 0 so (1-1) /2 is 0. index 2's parent is 0 so (2-1) /2 = 0. So yes the truncation is supposed to be there.

---

### Post by kavon89 on 2009-02-12
Well I ran your code through a debugger and the problem is with the way you are getting input from the user. Your code hangs on hasNextInt() after it goes through the one line input of integers from the user. Try this as a main class:

```
public class Driver {

    public static void main(String args[]){
        Heap heap = new Heap();
        Scanner input = new Scanner(System.in);
        System.out.println("how many numbers? ");
        int count = input.nextInt();

        for(int i = 0; i < count; i++) {
            System.out.print("enter an integer: ");
            heap.add(input.nextInt());
        }

        input.close();
        System.out.print("\nsorted integers: ");
        while(heap.getSize() > 0){
            int number = heap.removeFromHeap();
            System.out.print(number+" ");
        }

    }

}
```

---

### Post by shadylookin on 2009-02-12
ya that does make it work, thanks. Any clue as to why it hangs with input.hasNextInt() or even input.hasNext() ? I mean theoretically speaking it should leave the loop once there is no more input. For future reference it would be nice to know why this isn't working as it should

---

### Post by kavon89 on 2009-02-12
> Returns: true **if and only if** this scanner's next token is a valid int value 

I guess if the next token doesn't exist, it doesn't return anything and waits.


While going through the API I found a better method for your original code, [hasNext()]("http://java.sun.com/javase/6/docs/api/java/util/Scanner.html#hasNext()") seems to do what you want.

---

### Post by shadylookin on 2009-02-12
> **kavon89 said:**
> I guess if the next token doesn't exist, it doesn't return anything and waits.


While going through the API I found a better method for your original code, [hasNext()]("http://java.sun.com/javase/6/docs/api/java/util/Scanner.html#hasNext()") seems to do what you want.

I've tried that as well and it gets stuck also.

---

### Post by kavon89 on 2009-02-12
> **shadylookin said:**
> I've tried that as well and it gets stuck also.

> This method may block while waiting for input to scan.

:? Hrm... Try using hasNextInt() but after you're done typing integers with spaces between them, put a char or a string at the end.

 

The best way to do this in my mind would be to take the whole line as a string with next() and then split() the string into a String[], and finally convert the Strings to int, watching for exceptions.

---

### Post by eye208 on 2009-02-13
Replace this statement...
```
Scanner input = new Scanner(System.in);
```
... with this:
```
Scanner input = new Scanner(new BufferedReader(
    new InputStreamReader(System.in)).readLine());
```
Note that you have to import the java.io package and add a try/catch block for IOExceptions.

---

