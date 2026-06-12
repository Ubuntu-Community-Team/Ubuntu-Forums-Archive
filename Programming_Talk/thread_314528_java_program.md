---
title: "java program"
date: 2006-12-07
forum: Programming Talk
---

### Post by sailingboarder on 2006-12-07
i working on a simple(for now) program for a school project
it should ask the user a question pertaining to latin grammar, the user types the response, and then the program compares it to the correct response
the portion of my code that is not working correctly is the comparison of the two strings(the input and the stored correct answer)
```
 boolean whileB = true;
       while (whileB) {
           //randomly select parts of the question
           int nounint = rnums.nextInt(9);
           int vocabint = rnums.nextInt(noun.length);
           if (vocabint == 0)
                   vocabint++;
           if (vocabint == noun.length)
                   vocabint--;
           //prepare and ask the question
           String question = "What is the " + noun[0][nounint] + " of " + noun[vocabint][0] + "?";
           System.out.println(question);
           //read the input
           try{
               InputStreamReader converter = new InputStreamReader(System.in);
               BufferedReader in = new BufferedReader(converter);
               String answer = in.readLine();
           }catch(IOException e) {
               System.out.println(e);
           }
           //if user types q or quit, boolean will become false and while loop will quit, ending the program
           if (question.equalsIgnoreCase("q ") | question.equals("quit"))
               whileB = false;
           //if user enters correct answer, congradulate them then let while loop ask next question
           else if (question.equalsIgnoreCase(noun[vocabint][nounint]))
               System.out.println("Correct");
           //for the wrong answers, let it give them the correct answer and move on
           else
               System.out.println("Wrong! The correct answer is " + noun[vocabint][nounint]);
       }
```

---

### Post by Tomosaur on 2006-12-07
You don't have the curved braces around your if statement:
```

if (question.startsWith("q ") | question.equals("quit")) {
  whileB = false;
  //if user enters correct answer, congradulate them then let while loop ask next question
} else if (question.startsWith(noun[vocabint][nounint])) {
    System.out.println("Correct");
    //for the wrong answers, let it give them the correct answer and move on
} else {
  System.out.println("Wrong! The correct answer is " + noun[vocabint][nounint]); 
}

```

---

### Post by sailingboarder on 2006-12-07
ok, i'm feeling really stupid
while adding the brackets like u said, tomosaur, i discovered that i was comparing the question to the input and not the answer
so i changed that and now it works
now sure if the brackets made a difference or not, but i have them in now
thankyou tomosaur 

next time i'll just have to look over my code alittl closer before jumping to the forum

---

### Post by Tomosaur on 2006-12-07
Well let's put it this way, it definately doesn't work without the brackets :P

---

