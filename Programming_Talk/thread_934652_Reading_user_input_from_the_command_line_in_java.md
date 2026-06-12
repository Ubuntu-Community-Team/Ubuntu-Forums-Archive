---
title: "Reading user input from the command line in java"
date: 2008-09-30
forum: Programming Talk
---

### Post by shadylookin on 2008-09-30
I'm trying to write a program that takes input from the user from the command line and determine whether their input is a valid integer, real number, or identifier. I'm pretty sure this is more technically called a parser, but that's not so important. 

The problem I'm having is that using the Scanner class(java.util.Scanner) has been forbidden because it is too easy to ask for nextInt or nextDouble with the scanner. 

However the scanner is the only way I know to take user input from the command line, so what I need to know what are alternative ways to go about getting user input from the command line?

thanks for the help.

---

### Post by Lux Perpetua on 2008-09-30
Do you mean command line arguments? Those are just given to your main function as an array of strings. 

If you mean interactive input, then I suppose you can use System.in.read().

---

### Post by slavik on 2008-10-01
BufferedReader input = new BufferedReader(new InputStreamReader(System.in));
String line;

line = input.readLine();
while (!line.equals("")) {
//check line here ...
line = input.readLine();
}

---

