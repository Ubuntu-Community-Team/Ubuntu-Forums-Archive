---
title: "getting input from a txt file in java...."
date: 2009-03-28
forum: Programming Talk
---

### Post by Mia_tech on 2009-03-28
guys, I need suggestion on how I could get the input from a text file in Java, and separate the question from the answers..

```
Which Java keyword is used to define a subclass?
sub

What is the original name of the Java language?
A) *7
B) C--
C) Oak
D) Gosling
Select the best choice:
C
```

---

### Post by simeon87 on 2009-03-28
The answer to the first question is actually extends ;)

Anyway, it depends on how the file format is defined. If every question is on a single line and question/answer combinations are separated by an empty line, you could write code to parse that.

---

### Post by Mia_tech on 2009-03-28
> **simeon87 said:**
> The answer to the first question is actually extends ;)

I know you're looking at the questions and answer after the student has finished... so it contains some answer that are wrong

> Anyway, it depends on how the file format is defined. If every question is on a single line and question/answer combinations are separated by an empty line, you could write code to parse that.
OK, parsing when everything is in a single line is pretty easy, but how about when you have a multiple choice question when do you stop reading input?... take a look at the second question I posted

---

### Post by simeon87 on 2009-03-28
> **Mia_tech said:**
> OK, parsing when everything is in a single line is pretty easy, but how about when you have a multiple choice question when do you stop reading input?... take a look at the second question I posted

Until the end of the file or until the next empty line? That's why I said it depends on how the file format is defined. If you know for sure that every combination of question+answer does not contain empty lines, you can continue until you either hit the next empty line or until you hit the end of the file.

Basically, you're writing a parser now for a certain file format. Parsers use a formal grammar (see Wikipedia) to know what kind of input they can expect. Once you know the formal grammar, you know what the parser needs to do. You've given us two examples of what a question/answer pair could look like but we can't really answer the question without knowing exactly what the input looks like (or will look like for other questions).

If you can define the file format yourself, I'd simply use an empty line to separate the question/answers, then you can use the empty lines as separator when you're parsing the file.

---

### Post by Mia_tech on 2009-03-28
you're right, the separator is an empty line.. here's the file

```
Which Java keyword is used to define a subclass?
extends

What is the original name of the Java language?
A) *7
B) C--
C) Oak
D) Gosling
Select the best choice:
C

Which of the following types are supertypes of Rectangle?
A) PrintStream
B) Shape
C) RectangularShape
D) Object
E) String
Select all that apply:
BCD

What is the square root of 2?
1.4
```

---

### Post by simeon87 on 2009-03-28
Here's a possible way to parse the file:

```

import java.io.*;
import java.util.*;

public class Main {

	public static void main(String[] args) {
		String filename = ""; // fill in filename here
		try {
			// open file
			BufferedReader in = new BufferedReader(new FileReader(filename));
			
			// this list will store all the lines that belong to a single
			// question/answer
			ArrayList<String> questionAnswer = new ArrayList<String>();
			
			// read lines
			String line;
			while ((line = in.readLine()) != null) {
				
				// the line is empty, so the list now contains the lines
				// that belong to a single question/answer
				if (line.length() == 0) {
					
					// do something with the question
					processQuestion(questionAnswer);
					
					// clear the list so we can process more if needed
					questionAnswer.clear();
				} else {
					
					// the line is not empty so we add it to the list
					questionAnswer.add(line);
				}
			}
			
			// the end of the file can also be a separator so
			// if there are lines in the list, we need to process
			// those as well
			if (questionAnswer.size() > 0) {
				processQuestion(questionAnswer);
			}
			
		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
	
	// do something with the question
	public static void processQuestion(ArrayList<String> questionAnswer) {
		if (questionAnswer.size() >= 2) {
			System.out.println("-----");
			System.out.println("The question is: " + questionAnswer.get(0));
			
			if (questionAnswer.size() > 2) {
				System.out.println("The answer options are: ");
				for (int i = 1; i < questionAnswer.size() - 2; i++) {
					System.out.println(questionAnswer.get(i));
				}
			}
			
			System.out.println("The answer is: " + questionAnswer.get(questionAnswer.size() - 1));
		}
	}
}

```

Output:

```

-----
The question is: Which Java keyword is used to define a subclass?
The answer is: extends
-----
The question is: What is the original name of the Java language?
The answer options are: 
A) *7
B) C--
C) Oak
D) Gosling
The answer is: C
-----
The question is: Which of the following types are supertypes of Rectangle?
The answer options are: 
A) PrintStream
B) Shape
C) RectangularShape
D) Object
E) String
The answer is: BCD
-----
The question is: What is the square root of 2?
The answer is: 1.4

```

---

### Post by Mia_tech on 2009-03-28
wow, ok well done... thanks for the help now I have an idea of how to parse that empty line (line.lenght == 0)... but if I could use my own code would be a lot easier, but actually I've been given the runner/tester and have to design my code based on that... I don't want you do it for me, so don't post the code for it, but maybe you can help me decipher parts of the code I'm not getting... 

[PHP]Quiz q = new Quiz();
      Scanner in = new Scanner(new FileReader("quiz.txt"));
      q.read(in);
      in.close();

      in = new Scanner(System.in);

      ArrayList<Question> questions = q.getQuestions();
      ArrayList<String> answers = new ArrayList<String>();

      for (Question qu : questions)
      {
         System.out.println(qu.getText());
         String answer = in.nextLine();
         answers.add(answer);
      }

      boolean[] results = q.checkAnswers(answers);

      for (int i = 0; i < results.length; i++)
      {
         System.out.println() ;
         System.out. println(questions.get(i).getText());
         System.out.println("Correct answer: "
               + questions.get(i).getAnswer());
         System.out.println("Your answer: " + answers.get(i));
         System.out.print("Your answer was ");
         if (!results[i])
         {
            System.out.print("not ");
         }
         System.out.println("correct.");
      }[/PHP]

my first question comes with the construct of the ArrayList of type question which = q.getquestions() I've never seen it like this I've always seen something like ArrayList<question> question = new ArrayList<question>(), .. . Obviusly there are two other classes Quiz, and Question, I'm assuming that the getQuestion() method belongs to the Question class, but that declaration is the same as ArrayList<Question> question = new ArrayList<question>();

---

### Post by Mia_tech on 2009-03-28
oh, and in your code you don't parse the question from the answer, you assume that the answer is part of the question... in my design the I create an ArrayList that takes in question, and answer

[PHP]public Question(String question, String answer)
{
this.question = question;
this.answer = answer;
}
[/PHP]

also looking at the code above the first for loop present the user with a text in which the user actually takes the test and enter the answers, and the question is presented with a getText() method... I'm suspecting that the getText method is the one doin the parsing that or the qetQuestion method... that's where my confusion is

---

### Post by simeon87 on 2009-03-28
> **Mia_tech said:**
> my first question comes with the construct of the ArrayList of type question which = q.getquestions() I've never seen it like this I've always seen something like ArrayList<question> question = new ArrayList<question>(), .. . Obviusly there are two other classes Quiz, and Question, I'm assuming that the getQuestion() method belongs to the Question class, but that declaration is the same as ArrayList<Question> question = new ArrayList<question>();

From what I can see, the getQuestions() method belongs to the Quiz class (because it says q.getQuestions() and q is a Quiz) and it returns a ArrayList<Question>.

So in this case, it's not creating the ArrayList<Question> locally (using new ArrayList<Question>()) but it receives it from another class by calling getQuestions().

> **Mia_tech said:**
> oh, and in your code you don't parse the question from the answer, you assume that the answer is part of the question... in my design the I create an ArrayList that takes in question, and answer

That's better but I was just showing how the file could be read so adding more classing would only make it larger. But in a real application, a Question class would make sense to group the question and the answer together.

---

### Post by simeon87 on 2009-03-28
> **Mia_tech said:**
> also looking at the code above the first for loop present the user with a text in which the user actually takes the test and enter the answers, and the question is presented with a getText() method... I'm suspecting that the getText method is the one doin the parsing that or the qetQuestion method... that's where my confusion is

Your code is an interactive program that allows the user to type in their answer after a question has been presented. In my code, it's reading everything from a file and then separates the questions and the answers. It should be clear that they're not doing the same parsing. In the code you posted, I think it's only doing some (limited) parsing in the method q.checkAnswers(answers); as this method receives a list of answers (Strings) to check whether they're correct or not.

In Java get___ methods (e.g., getText, getQuestions) generally don't do anything other than returning a value so I don't think there's parsing going on there.

---

### Post by Mia_tech on 2009-03-28
I originally thought the same thing that q.getQuestion() it was part of the Quiz class, but been getQuestion should really belong in the Question class, that is if you want your classes to be "cohesive" and minimize coupling between them, but I thought well maybe Quiz is inheriting from Questions, but I don't see the need for super classes.. as far as parsing yes there's some as at some point you would have to parse the question from the answer before storing into arrylist

---

### Post by Mia_tech on 2009-03-28
> **simeon87 said:**
> From what I can see, the getQuestions() method belongs to the Quiz class (because it says q.getQuestions() and q is a Quiz) and it returns a ArrayList<Question>.

So in this case, it's not creating the ArrayList<Question> locally (using new ArrayList<Question>()) but it receives it from another class by calling getQuestions().


yes, That's what I thought that the ArrayList probably was declare in some other class

---

### Post by Mia_tech on 2009-03-28
does anyone have any idea what the getQuestions() method has?

---

### Post by HotCupOfJava on 2009-03-28
Maybe I've read too fast, and don't really understand the problem....

Are you trying to figure out how getQuestions() knows the difference between the question and the answer? If so, I've noticed that each question ends with a question mark....

I'm really not trying to be a smart-@$$, I promise.:)

---

