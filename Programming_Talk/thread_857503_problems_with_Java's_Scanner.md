---
title: "problems with Java's Scanner"
date: 2008-07-12
forum: Programming Talk
---

### Post by shadylookin on 2008-07-12
I'm having a problem with the Scanner class in java(at least I think so). Whenever I ask for user input from the keyboard none of my if and else if statements are properly recognizing the String from the scanner.

for instance when I have command = userInput.next();
even if the String perfectly matches the word "quit"(without quotations) that is supposed to set the boolean running equal to false the if statement fails to run. 

Also when I type "insert"(w/o quotations) the else if statement that checks to see if command == "insert" fails to execute. I've checked the debugger and the variable command is correct. 

So what am I doing that's causing this problem?

thanks for the help 

here's the code I'm having difficulty with
```
import java.util.Scanner;
import java.io.File;


public class Hash {
	
	**private Scanner userInput = new Scanner(System.in);**
	private LinkedList[] hashTable = new LinkedList[17];
	
	public Hash(){
		// initialize the hashTable
		for(int i = 0; i<17; i++){
			hashTable[i] = new LinkedList();
		}
	}
	
	public static void main(String args[]){
		Hash hash = new Hash();
		hash.welcomeMessage();
		
	}// end main
	
	/**
	 * welcomeMessage prints a message that gives a description and a list of commands
	 * the user can input. then it gives a prompt asking for a command and then 
	 * gives that command to userCommand. 
	 * Valid commands are insert delete search save quit and load.
	 *
	 */
	public void welcomeMessage(){
		boolean running = true;
		String command;
		System.out.println("This program creates and loads a hash table that uses linking" +
				" that allows you to insert delete search save quit and load");
		
		while(running == true){
			System.out.print("enter command > ");
			**command = userInput.next();**
			**if(command == "quit"){**
				**running = false;//if command is quit then quit the loop**
			}
			else{
				userCommand(command);
			}
		}//end while loop
	}// end welcome message
	
	public void userCommand(String command){
		String in;
		int inInt;
		if(command == "save"){
			System.out.print("enter the name to save under >");
			in = userInput.next();
			save(in);
		}
		else if(command == "load"){
			System.out.print("enter the file to load >");
			in = userInput.next();
			load(in);
		}
		else if(command == "insert"){
			System.out.print("enter the integer to insert >");
			inInt = userInput.nextInt();
			insert(inInt);
		}
		else if(command == "delete"){
			System.out.print("enter the integer to delete >");
			inInt = userInput.nextInt();
			delete(inInt);
		}
		else if(command == "search"){
			System.out.print("enter the integer to search for >");
			inInt = userInput.nextInt();
			search(inInt);
		}
		else{
			System.out.println("invalid command");
		}
	}// end userCommand
	
	public void insert(int valueToInsert){
		int key = valueToInsert % 17;
		System.out.println(hashTable[key].add(valueToInsert));
	}// end insert
	
	public void search(int valueToSearchFor){
		
	}// end search
	
	public void delete(int valueToDelete){
		
	}// end delete
	
	public void save(String valueToSaveAs){
		
	}// end save
	
	public void load(String valueToLoad){
		
	}// end load
	
}// end class

```

---

### Post by Phristen on 2008-07-12
You can't compare strings with == in Java...
Use String.equals() method.

For example, "quit".equals("quit") will be true, but "quit" == "quit" won't.

---

### Post by shadylookin on 2008-07-12
Eureka it works. Thanks for the help.

---

### Post by kavon89 on 2008-07-12
To compare a string and ignore case, use:

```
if(input.equalsIgnoreCase("quit")) {
    //stuff
}
```

I would recommend using that since it looks like your program would be taking lots of input from the user.

---

### Post by ceclauson on 2008-07-13
This is true, you should be using the equals() method to compare strings for equality of content, not ==.

Two other thoughts.  First, the scanner class has a number of methods for parsing the next element of input.  In the context that you seem to be using it, you probably want to use nextLine() instead of next().  I think next() only gets the next whitespace delimited token.  I'm not sure that that would be significant in this context, but it might be.

Second, whenever I do what you're doing, I usually use the String class's trim() method before doing the comparison.  This eliminates leading and trailing whitespace.  Again, I don't know if this would be significant in this context, but it might be.

So here are the lines of code that you emphasized as I would write them:
```

	command = userInput.nextLine().trim();
	if(command.equals("quit")){
		running = false;//if command is quit then quit the loop
	}

```

I would try that, and if that doesn't work, post again :-)

---

