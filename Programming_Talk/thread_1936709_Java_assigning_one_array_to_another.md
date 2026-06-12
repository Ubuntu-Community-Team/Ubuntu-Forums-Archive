---
title: "Java: assigning one array to another"
date: 2012-03-06
forum: Programming Talk
---

### Post by Tk007LwZFJW5ej on 2012-03-06
The problem: questionHistory is a 100 by 5 integer array for storing data pertaining to 100 math questions. in my main method, some of the questionHistory array elements are being overwritten as the program runs, and I can't figure out how/why. operationClasses is an array of MathOperation objects (Addition, Subtraction, etc., which have no pertinent functionality, and for which MathOperation is a base class).

```

for ( numberOfQuesAnswered = 0; numberOfQuesAnswered < numQues2Record; numberOfQuesAnswered++ ){

     int nextOp = randomOperation.nextInt( operationClasses.length );
     //randomly choose an integer with which to index an operation from the array of math operations

     //begin generation of one question with the selected math operation    
     questionHistory[numberOfQuesAnswered]   =  operationClasses[nextOp].quiz();
}

```To check what is being stored in questionHistory, I added the following nested for loop right after that last statement (within the for loop above):

```

 for(int q = 0 ; q <= numberOfQuesAnswered;  q++){
        for(int j = 0; j < MathOperation.mathArraySize; j++)
            System.out.println(questionHistory[q][j]);
     }

```Here is the output of one run:

```

this is ques#: 0
-----------------------------------
How much is 11 plus 7?
Enter your answer (-1 to exit).
18
Keep up the good work!
11
7
1
18
18
this is ques#: 1
-----------------------------------
How much is 16 divided by 17?
Enter your answer (-1 to exit).
0
Keep up the good work!

11
7
1
18
18
16
17
4
0
0
this is ques#: 2
-----------------------------------
How much is 5 divided by 11?
Enter your answer (-1 to exit).
0
Keep up the good work!

11
7
1
18
18
5
11
4
0
0
5
11
4
0
0

```Notice the 3rd question that was asked overwrote data for the second question asked!

More detail:
I have a MathOperation class that basically creates and returns a 1 by 5 array representing a math problem with its quiz() method. Here is the quiz method (note method checkResponse() takes the user's answer input):

```

Random pickOperand = new Random();
   numbers[FIRSTOPERAND] = pickOperand.nextInt(maxIntSize   +  1);    //randomly select first integer operand between 0 and maxIntSize
   numbers[SECONDOPERAND] = pickOperand.nextInt(maxIntSize   +  1);    //randomly select second integer operand between 0 and maxIntSize
   numbers[OPERATION] = operationNumber;

   switch(numbers[OPERATION]){                                            //store correct answer in array
      case 1: numbers[CORRECTANSWER] = numbers[FIRSTOPERAND] + numbers[SECONDOPERAND];
         break;
      case 2: numbers[CORRECTANSWER] = numbers[FIRSTOPERAND] - numbers[SECONDOPERAND];
         break;
      case 3: numbers[CORRECTANSWER] = numbers[FIRSTOPERAND] * numbers[SECONDOPERAND];
         break;
      case 4: {
         while( numbers[SECONDOPERAND] == 0 ){           //regenerate 2nd operand to avoid division by zero
            numbers[SECONDOPERAND] = pickOperand.nextInt(maxIntSize   +  1);
         }
         numbers[CORRECTANSWER] = numbers[FIRSTOPERAND] / numbers[SECONDOPERAND];
      }
         break;
   }
   createQuestion(); //print math question to screen with appropriate operation symbol
   checkResponse(); //check if user response matches system-generated response

   return numbers;

```Here is class MathTest, which contains the main method:
```

public class MathTest {
   
   final static int numQues2Record = 100; //maximum number of questions to be recorded
   static int[][] questionHistory = new int[numQues2Record][MathOperation.mathArraySize];
   static int numberOfQuesAnswered;

   public static void main(String[] args){

   //instantiate math operation classes
   Addition add = new Addition();
   Subtraction subt = new Subtraction();
   Multiplication mult = new Multiplication();
   Division div = new Division();
   Random randomOperation = new Random(); //randomly chooses an operation: +, -, *, or / based on random int

   //store math operation classes in an array to facilitate randomly choosing an operation
   MathOperation[] operationClasses = {add, subt, mult, div};

  for ( numberOfQuesAnswered = 0; numberOfQuesAnswered < numQues2Record; numberOfQuesAnswered++ ){

     int nextOp = randomOperation.nextInt( operationClasses.length );
     //randomly choose an integer with which to index an operation from the array of math operations

     //begin generation of one question with the selected math operation    
     questionHistory[numberOfQuesAnswered]   =  operationClasses[nextOp].quiz();

```

---

### Post by dwhitney67 on 2012-03-06
Thanks for the inspiration (or should I thank your teacher?).

Anyhow, this is what I came up with:
```

import java.util.Random;
import java.io.Console;


class MathProblemGenerator
{
    Random random = new Random();
    int    maxValue;

    static final String operations = "+-*/";
    static final int    numOps = operations.length();

    public class MathProblem
    {
        private Console console = System.console();
        private String  equation;
        private int     result;
        private int     answer;

        public void promptForAnswer()
        {
            while (true)
            {
                try
                {
                    console.printf("\nQuestion:  " + equation + "\n");
                    String input = console.readLine("Answer?    ");
                    answer = Integer.parseInt(input);
                    break;
                }
                catch (NumberFormatException e)
                {
                    console.printf("A number is required!  Try again...\n\n");
                }
            }
        }

        public void showResult()
        {
            if (isCorrect())
            {
                console.printf("\nYour answer is correct!\n");
            }
            else
            {
                console.printf("\nYour answer is wrong (correct answer is " + result + ")\n");
            }
        }

        private boolean isCorrect()
        {
            return answer == result;
        }
    }

    public MathProblemGenerator(int maxVal)
    {
        maxValue = maxVal;
    }

    public MathProblem next()
    {
        int  val1 = random.nextInt(maxValue);
        int  val2 = random.nextInt(maxValue);
        char op   = operations.charAt(random.nextInt(numOps));

        if (op == '/' && val2 == 0)
        {
            while (val2 == 0)
            {
                val2 = random.nextInt(maxValue);
            }
        }

        MathProblem problem = new MathProblem();

        problem.equation = "" + val1 + " " + op + " " + val2;
        problem.answer   = 0;

        switch (op)
        {
            case '+': problem.result = val1 + val2; break;
            case '-': problem.result = val1 - val2; break;
            case '*': problem.result = val1 * val2; break;
            case '/': problem.result = val1 / val2; break;
        }

        return problem;
    }
}

public class MathTest
{
    public static void main(String[] args)
    {
        // Generator of math problems using values no greater than 50.
        MathProblemGenerator generator = new MathProblemGenerator(50);

        // Declare an array to store the generated math problems
        MathProblemGenerator.MathProblem[] problems = new MathProblemGenerator.MathProblem[5];

        // Generate math questions, and prompt user to answer each
        for (int i = 0; i < problems.length; ++i)
        {
            problems[i] = generator.next();
            problems[i].promptForAnswer();
            problems[i].showResult();
        }
    }
}

```
I personally had no reason to store each problem that is generated within an array, and frankly I'm not sure why you must do it.  But I'm sure you have unique requirements.

---

### Post by Some Penguin on 2012-03-07
OP:

(1) Next time, don't omit critical details like where you declare variables you're returning.

(2) There's a difference between 'assign' and 'copy'.  Judging from behavior, there's a pretty good chance you're just using the same numbers[] array ALL THE TIME.  Don't do that.

---

### Post by Tk007LwZFJW5ej on 2012-03-07
> **Some Penguin said:**
> OP:

(1) Next time, don't omit critical details like where you declare variables you're returning.


If you mean numbers[], it is declared in the method quiz.
> 
(2) There's a difference between 'assign' and 'copy'.  Judging from behavior, there's a pretty good chance you're just using the same numbers[] array ALL THE TIME.  Don't do that.

Your suggestions are too vague. I don't understand why I wouldn't use numbers[] "all the time" - it's a local variable that is essentially recreated every time the method is called. It seems like you only took a cursory look at the post.

---

