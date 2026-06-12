---
title: "Java RMI help needed."
date: 2007-02-20
forum: Programming Talk
---

### Post by flinty on 2007-02-20
I have been given the task to implement a client-server communication in the form of a multiple choice question. below is my code and the error i seem to keep getting can anyone help, or even tell me if im on the right lines. Though im quite sure i am. Im just new to RMI and am a little lost.

import java.rmi.*;


public class MCQClient {    
    
  public static void main(String[] args) {
    try {
      remoteMCQ sgen = (remoteMCQ) Naming.lookup("rmi://localhost/answer"); 
      System.out.println("The Question and possiable answers are as follows"+sgen.getQuestion());  
      System.out.println("Please select your choice of answer"+sgen.selectAnswer());**[COLOR="Red"]//error over selectAnswer() since it contains an int[/COLOR]**
      System.out.println("The correct answer was"+sgen.getCorrectAnswer());
    
    }
    catch(Exception e) {
      System.out.println("Problem encountered accessing remote object "+e);
    }	
  }
}


import java.rmi.*; [COLOR="Red"]**// all of this is fine**[/COLOR]

public interface remoteMCQ extends Remote 
{
    public String getQuestion() throws RemoteException;
    public void selectAnswer(int answer) throws RemoteException;
    public int getCorrectAnswer() throws RemoteException;
}


**[COLOR="Red"]//compiles fine!!![/COLOR]**
import java.rmi.*;
import java.rmi.server.UnicastRemoteObject; 
import java.util.*;    
 
   
 public class remoteMCQImpl extends UnicastRemoteObject implements remoteMCQ{

  public static Scanner input = new Scanner(System.in);

      public remoteMCQImpl() throws RemoteException { };
      public String getQuestion() throws RemoteException {	
 	//The method Question returns the question and possiable answers
	String Question = "Who has won the european cup the most amount of times?" +
	                  "1) Liverpool"+
			  "2) Man utd" +
			  "3) Notts Forest" +
			  "4) Mansfield Town" +
			  "5) Chelsea";
	return(Question);
      };
      
      public void selectAnswer(int answer) throws RemoteException {
	      answer = input.nextInt();
	
	}
	public int getCorrectAnswer() throws RemoteException {
	//The method CorrectAnswer fetches the correct answer
	int CorrectAnswer = 1;
	return(CorrectAnswer);
	} 
}

**[COLOR="Red"]//compiles fine!!![/COLOR]**
import java.rmi.Naming;

public class Server{
  public static void main(String[] args) {
    try {
      remoteMCQImpl remote = new remoteMCQImpl();
      Naming.rebind ("Dater", remote);
      System.out.println("Object bound to name");
    }
    catch(Exception e) {
      System.out.println("Error occurred at server  "+e.getMessage());
    }
 }
}

---

### Post by Tomosaur on 2007-02-21
You need to get an integer from standard input, and pass it to the selectAnswer(int) method.
You need to
```
import java.util.Scanner;
```
Instantiate it:
```

private Scanner input = new Scanner(System.in);

```
And then get the input:
```

int my_int = input.nextInt();
System.out.println("Please select your choice of answer"+sgen.selectAnswer(my_int));

```

---

### Post by flinty on 2007-02-21
thank you for the help but once i followed what you said it brought about the error below tried to work out why the error is happening but still cant work it out any help would be appreiciated:

C:\Documents and Settings\Dan\My Documents\Work\comp212>javac MCQClient.java
MCQClient.java:17: 'void' type not allowed here
      System.out.println("Please select your choice of answer"+sgen.selectAnswer
(input_ans));
                         ^
1 error

import java.rmi.*;
import java.util.*;


public class MCQClient {    
	
  private static Scanner input = new Scanner(System.in);	
    
  public static void main(String[] args) {
	 
    try {
      remoteMCQ sgen = (remoteMCQ) Naming.lookup("rmi://localhost/answer"); 
      System.out.println("The Question and possiable answers are as follows"+sgen.getQuestion());  
      System.out.println("Please select your choice of answer");
      int input_ans = input.nextInt();
      System.out.println("Please select your choice of answer"+sgen.selectAnswer(input_ans));
      System.out.println("The correct answer was"+sgen.getCorrectAnswer());
    
    }
    catch(Exception e) {
      System.out.println("Problem encountered accessing remote object "+e);
    }	
  }
}

---

### Post by Tomosaur on 2007-02-21
My mistake. Are you sure you're doing this right? Your selectAnswer method is only taking user input - so why does it need to receive an integer?

In any case, you can fix this error by replacing the 'void' with 'int' here:
```

public void selectAnswer(int answer) throws RemoteException {
answer = input.nextInt();
}

```
but this will also need you to return an integer, so your code will look like this:
```

public int selectAnswer(int answer) throws RemoteException {
answer = input.nextInt();
return answer;
}

```
This makes no sense though. This method takes an int which you got from input, then takes input again, and returns it. You may aswell just scrap this selectAnswer method, and use this line in your main method instead.
```

System.out.println("Please select your choice of answer "+input.nextInt());

```
But this, too, is pretty pointless, and doesn't do much.

---

### Post by flinty on 2007-02-21
Sorry to be a pain! I've resolved the issue now. all compiles as it should but when running the server i get this error:

C:\Documents and Settings\Dan\My Documents\Work\comp212>java Server
Error occurred at server  RemoteException occurred in server thread; nested exce
ption is:
        java.rmi.UnmarshalException: error unmarshalling arguments; nested excep
tion is:
        java.lang.ClassNotFoundException: remoteMCQ

any ideas why?

Dan

---

### Post by Tomosaur on 2007-02-21
You need to include the remoteMCQ interface class in the directory where the server class files are.

---

### Post by flinty on 2007-02-21
It is in the same directory so i aint got a clue!

dan

---

### Post by Tomosaur on 2007-02-21
Bit weird. Did you run:
```

rmic remoteMCQImp
rmiregistry
java server

```

The stub class created by rmic needs to go with the client class files.

---

### Post by flinty on 2007-02-21
The first step creates an error saying that the class file is not there but it is?!

---

### Post by Tomosaur on 2007-02-21
> **flinty said:**
> The first step creates an error saying that the class file is not there but it is?!

Sorry, misspelled it. It should be the name of the class which implements remoteMCQ, so it's:
```

rmic remoteMCQImpl

```

---

### Post by flinty on 2007-02-21
i saw the error u made and tried it that way still the same error!?

dan

---

### Post by Tomosaur on 2007-02-21
Try it with this command:
```

java -cp . server

```

---

