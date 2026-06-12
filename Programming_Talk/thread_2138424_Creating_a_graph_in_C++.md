---
title: "Creating a graph in C++"
date: 2013-04-24
forum: Programming Talk
---

### Post by Amulon on 2013-04-24
[COLOR=#000000][FONT=verdana]So I have been trying to find a good place to learn how to implement a graph, but I have been unable to find one. [/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I have to create a program that reads in the data about airports and the airports that they are connected to. And the goal of the program is to find the least expense way to go from point A to point B. My question is, how do I put in the data from a file and make a graph out of it? Below is my code to read in the file. [/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Thanks a bunch for looking over this. I just don't really understand how to input data into a graph and be able to get information from it. Thanks again

[/FONT][/COLOR]```
[COLOR=#000000]    [/COLOR]while[COLOR=#000000] (!textFile.eof())[/COLOR]
{        
textFile >> startAirport >> endAirport >> milege >> cost;        
cout << startAirport <<  " " << endAirport <<  " " << milege <<  " $" << cost << endl; 
[COLOR=#000000] }[/COLOR]
```[COLOR=#000000][FONT=verdana]
[/FONT][/COLOR]

---

### Post by JDShu on 2013-04-24
The main ways to implement a graph are: 2D matrix, objects and pointers, and adjacency lists. This is pretty fundamental stuff so you should be able to find a lot of resources using your favourite search engine.

---

### Post by alan9800 on 2013-04-24
Perhaps [mathgl tools](https://launchpad.net/ubuntu/+source/mathgl/1.11.2-16) might be somehow helpful for you.

---

### Post by Mr.Pytagoras on 2013-04-24
You can use lists, you will have an airport A and from that you could get to B, C and D then in your reprezentation it would look like this:
Create a node A -> let say a class or struct, that contain a list of airport where can you go in this case the list will contain B, C, D

do this for every airport and you have one reprezentation of a graph

---

### Post by Amulon on 2013-04-24
Awesome! Thanks guys for your input. It shed some more light on this program and its helped me get closer to finishing. Thanks again!

---

### Post by Amulon on 2013-04-24
Thread reopened! Okay, so i've done something like this

```
[COLOR=#000000][FONT=verdana]struct flight[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]{[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]string startAirport;[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]string endAirport; [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]int milege;[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]int cost;[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]}[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]int main ()[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]{[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]flight f;[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]vector <flight> sky;[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]//read data from file[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]textFile>>f.startAirport >> f.endAirport >>f.milege>> f.cost;[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]sky.push_back (f)[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]}[/FONT][/COLOR]
```

[FONT=verdana, arial, helvetica, sans-serif][COLOR=#000000]Sorry if I seem like an idiot... because with nodes and stuff its true. Hah. Like, I understand that I will be identifying the startAirport as node 1, and then check all the other nodes for the cheapest flight. Basically, I don't know how to manage/organize the information I get. Like what to do with it after it is in the vector/list to make it all connected. If you could provide me with an example or something to help me with this I would greatly appreciate it.[/COLOR][/FONT]

---

### Post by Amulon on 2013-04-24
[COLOR=#000000][FONT=verdana]So would I not create this at the start? Because the user has to enter in which airport they want to start the flight. Then the rest of the information will be displayed about all possible routes and which one is the cheapest. So wouldn't I have to store all the info and then put it in the 'struct flight' according to the user input? How would I store it so I can ask the user for input, then do if (input = "DEN") then I would make denver node #1 and do the rest of the algorithm according to that. I just don't know how to store the information in a good way and then beable to access it when the user asks for it[/FONT][/COLOR]

---

