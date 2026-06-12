---
title: "Referencing positions in arrays (Java)"
date: 2010-04-13
forum: Programming Talk
---

### Post by Ravenshade on 2010-04-13
The code is below. 

Now I realise that initialising the variables a & b are overwriting what I want to do. Yet I can't find another solution. 

I want to be able to cycle through the positions in the array using the while loop. At least thats how my mind is working at the moment. Let me explain a few details about the code. 

Variables

a        is supposed to function as the reference to a position. Thereby being array[0] or 
         array[1] without being the actual value. (The values being 17 and 6 respectively)

b        is the next number in the array. In theory a+1. 

i         i is merely for another loop further down in the code which isn't causing a
          problem 

At this version of the code I am trying to use System.arraycopy however I have also tried to assign the values manually. (aka, finalNum[a] = numeral[a]) However the positions always return 0. 

Now I took out the 0 from int a = 0; However I get the error that 'a might not be initialised'. 

Any tips? :popcorn: < free popcorn for anyone who wants it




```
/*Documentation
  a) Given a list of integers, removes all the duplicates from the list. For example, the list:

    17   6   45   2   3   17   6   9   8   6    1   4   12
    after removing the duplicates becomes:

    17   6    45   2   3   9   8   1   4   12
 
 This program solves the problem for all positive integers. 
 
null = -1
     */
     
class problem1c {

    public static void main(String[] args) {
    
        //initialise while -1 loop. 
        int a = 0;
        int b = 1;
        int i = 1; //start while loop at 1. 
        
        //Declare the initial array
        int[] numeral = { 17, 6, 45, 2, 3, 17, 6, 9, 8, 6, 1, 4, 12};
        int[] finalNum = new int[13]; //define as empty to be filled. 
        
        //check the array. 
        while (numeral[a] < (numeral.length)) {
            if (numeral[a] != -1) { //if not equal to minus 1, continue, else increment. 
                while (numeral[b] <= (numeral.length)) {
                                    //What about numeral B? what if it already is -1?
                    if (numeral[a] == numeral[b]) { //Check if numeral a and subsequent are similar
                        numeral[b] = -1;     //if TRUE then erase secondary number. 
                    }
                                    //else
                    b++;                //Increment b to check 
                                    //the next number in he sequence
                }
                    System.arraycopy(numeral, a, finalNum, a, 1); //copy over
                    a++;
                    //increment a for the next number in the sequence
            } else {
            
            a++;
            }
            
        }
        
        while (i < finalNum.length) {
         
                //System.out.println(finalNum[i]);
                System.out.println(finalNum[i]);
            
            
            i++; //increment while loop to end!
        }
    
    }

}
```

---

### Post by zoff_ita on 2010-04-13
You don't need to save the pointer, you simply need the index.

Why don't you use for cycle instead of while?

This is a working code:
```
/*Documentation
  a) Given a list of integers, removes all the duplicates from the list. For example, the list:

    17   6   45   2   3   17   6   9   8   6    1   4   12
    after removing the duplicates becomes:

    17   6    45   2   3   9   8   1   4   12
 
 This program solves the problem for all positive integers. 
 
null = -1
     */
     
class problem1c {
	
    public static void main(String[] args) {

        //Declare the initial array
        int[] numeral = { 17, 6, 45, 2, 3, 17, 6, 9, 8, 6, 1, 4, 12};
        int[] finalNum = new int[13]; //define as empty to be filled.
        
        boolean hasBeenCopied = false;
        int nCopiedItems = 0;
        //Check all numeral's items
        for(int i=0; i<numeral.length; i++){
        	hasBeenCopied = false;
        	//Cycle destination array
        	for(int j=0; j<nCopiedItems; j++){
        		//Check if current item in destination array is equals to current item in source array
        		//This means that this number has been copied before
        		if( numeral[i]==finalNum[j]){
        			hasBeenCopied=true;
        			break;
        		}
        	}
        	if(!hasBeenCopied){
        		//Copy current number into destination array
        		finalNum[nCopiedItems++] = numeral[i];
        	}
        }
        int i=0;
        while (i < finalNum.length) {
            //System.out.println(finalNum[i]);
            System.out.println(finalNum[i]);
            i++; //increment while loop to end!
        }
    
    }

}
```

To get a better code you can create a method to check if an item is already contained in destination array and use foreach syntax.

For example:
```
/*Documentation
  a) Given a list of integers, removes all the duplicates from the list. For example, the list:

    17   6   45   2   3   17   6   9   8   6    1   4   12
    after removing the duplicates becomes:

    17   6    45   2   3   9   8   1   4   12
 
 This program solves the problem for all positive integers. 
 
null = -1
     */
     
class problem1c {
	
	public static boolean contains(int elem, int[] array){
		for(int i:array){
			if(i==elem){
				return true;
			}
		}
		return false;
	}
	
    public static void main(String[] args) {

        //Declare the initial array
        int[] numeral = { 17, 6, 45, 2, 3, 17, 6, 9, 8, 6, 1, 4, 12};
        int[] finalNum = new int[13]; //define as empty to be filled.
        
        int nCopiedItems = 0;
        //Check all numeral's items
        for(int num: numeral){
        	//Check if current number has been copied before
        	if(!contains(num, finalNum)){
        		//Copy current number into destination array
        		finalNum[nCopiedItems++] = num;
        	}
        }
        
        for (int i=0;i < finalNum.length; i++) {
            System.out.println(finalNum[i]);
        }
    
    }

}
```

---

### Post by Ravenshade on 2010-04-13
For is restrictive, the while loop is flexible. I'm not exactly certain which numbers will be entered into the program, depends on what data I get from another program. 

And what pointer >_> I wasn't aware that Java used pointers. 

However thanks for the code, I'll compile and work through, thank you for your time. *hands out free popcorn*

Edit

I wanna be as smart as the guy above me. >_> Why why can't I think outside of the box!

---

### Post by Reiger on 2010-04-13
The problem is homework and this is not a course forum.

However, a few tips to save you a few future wheel implementations:
[list="1"]
[*]Consider using the convenience methods in Arrays and Collections classes. (Note the plural spelling.)
[*]Read up on the Java Collections framework. If you knew that framework and you could have implemented this in about 5 lines of code.
[/list]

```

import java.util.*;

public static void main(String[] args) {
  int[] numeral = { 17, 6, 45, 2, 3, 17, 6, 9, 8, 6, 1, 4, 12};
  Set<Integer> set=new HashSet<Integer>();
  set.addAll(Arrays.asList(numeral));
  Integer[] results = set.toArray(new Integer[set.size()]);
  
  // print results.
  for(Integer result: results) {
    System.out.println(result);
  }
}

```

---

