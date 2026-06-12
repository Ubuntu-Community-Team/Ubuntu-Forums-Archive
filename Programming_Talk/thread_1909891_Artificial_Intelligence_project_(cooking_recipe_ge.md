---
title: "Artificial Intelligence project (cooking recipe generator)"
date: 2012-01-16
forum: Programming Talk
---

### Post by RobikShrestha on 2012-01-16
I need to build an AI project. We are learning AI this semester. Till now I know some basic stuff about programming in prolog and about expert systems.
[B]
My idea:[/B]

The software I am thinking of should have the following features:

1. Take in a recipe from the user and assign a score to the recipe. (based on combination of ingredients, cooking time and recipes stored in a database)

2. Take in an incomplete recipe and complete it (i.e. correct/complete the dish)

**Problem I am having:**

The features I am thinking of are really vague and ill-defined. I want some concrete problem statements. But I am finding it really difficult to define problem statements. The project is due in about 2 months. I want a scaled down project (may be with much more constrained features).  Please help me in defining a **problem statement** which is doable in the given time. (But it should still remain interesting!!)


In short, I have an idea, but I need a realistic problem statement. Thanks.

---

### Post by RobikShrestha on 2012-01-16
I am thinking of storing

1. Ingredients
2. Pairs of ingredients which go well together
3. Pairs of ingredients which are disastrous together

I need more ideas!

---

### Post by RobikShrestha on 2012-01-16
If you think that my idea is too vague or stupid then please give me some other ideas for the project.

---

### Post by lisati on 2012-01-16
Please be patient, I haven't seen that many discussions of AI in the time I've been participating here.

---

### Post by RobikShrestha on 2012-01-16
Ok, I am being patient.
I can't get much help in google either, just needs some specific problems/solutions to my idea.

---

### Post by tjoff on 2012-01-16
It is a fascinating topic. I understand your difficulty in defining a good problem statement, it lies in the nature of the subject that "in matters of taste there is no dispute". 
I do not know if you are familiar with the following paper: [http://arxiv.org/abs/1111.6074](http://arxiv.org/abs/1111.6074)
but you might get some inspiration from that.
I am almost 100% percent sure you already know [http://www.xkcd.com/720](http://www.xkcd.com/720)
but just in case ...

---

### Post by RobikShrestha on 2012-01-16
Yeah thanks for the links esp: for the paper. But I am still struggling with the problem statement.

---

### Post by Tony Flury on 2012-01-16
Actually a far more useful functionality would be along the lines of : 
"Given all the stuff i have in my fridge/cupboard, give me a recipe that I can prepare".

The above is actually a pretty complex question and the results can be optimised in a number of ways - preparation time, personal taste, skill level etc.

I can't help you with a "problem statement" per-se - I am used to defining the fuctionality I need in terms of Agile User stories - for instance : 

Story 1 : 
As a person wanting to prepare a meal
I want to be provided with a list of meals which I can prepare based on the ingedients I have at my disposal
So that I can cook my meal within the time, cost and skill constraints I have and without needing extra shopping trips.

Whether this style is useful to you I don't know.

---

### Post by RobikShrestha on 2012-01-16
Brilliant!! I think your idea is really good. 
Now I should learn features of AI. May be I will learn more about expert systems and then design a solution for that. Thanks a lot!!

---

### Post by tjoff on 2012-01-16
In supplement to Tony Flury:

Story 2:
Another person likes cooking trying out new exciting recipes, but often lacks one or more ingredients.
He often asks himself questions like: "This recipe contains lime juice, but I don't have that. Can I replace it with cod liver oil? Or maybe leave it out entirely? Gee, I wish there was an app for that..."

---

### Post by RobikShrestha on 2012-01-16
That is a really good idea too! Even I have often had those sort of confusions especially while making pizza. Eg: can I use certain kind of cheese instead of the one mentioned in the recipe. And if so, is there any change needed in the recipe?



Keep those ideas coming!!

---

### Post by tbastian on 2012-01-16
I find this thread to be very interesting! I have thought about doing this exact thing, but have never had the time to make it. You should let us know how it turns out! I wouldn't mind a copy of your program when you're done (if you're allowed/want to share it)!

---

### Post by RobikShrestha on 2012-01-16
Of course I would love to share it. 

Free and open source softwares that's what linux is all about.



Keep those ideas coming!!

---

### Post by RobikShrestha on 2012-01-16
Now I have got other ideas.
The application should judge habits (examples are given below)

1. student's study habits

2. employee's working habits

3. health habits (like lumosity)

May be use a detailed questionnaire

Now my question:

Cooking vs the topics i just mentioned: Which would be a better AI project? Please give reasons too!!

---

### Post by RobikShrestha on 2012-01-16
**@**[Tony Flury]("http://ubuntuforums.org/member.php?u=591713")

[B]What I think is the way to go:
[/B]
1. Store recipes which provide the details about cooking time, ingredients(with quantities) and skill level.
2. Ask the users for all those details and find the appropriate recipes. 

**Now this is bothering me:**

If the recipes themselves provide such details, wouldn't my solution be just an advanced search? What should I do to make it an AI project?
 (i.e. add some kind of intelligence or learning mechanism to it so that I could make a cool project!!)

---

### Post by Tony Flury on 2012-01-16
@RobikShrestha - sorry but I know very little about AI, but here goes: even if you did this as a big search, there would have to be an element of fuzzy logic (which is elated to AI) to find semi-perfect matches - for instance it is reasonable to assume that some ingredients are easy to get (eggs, flour) so if a recipe needs those you could ignore them for the "no shopping" rule, but for other items (spices, exotic vegetables you might not be able to ignore them).

I see this as a decision tree - rather than a search.

The Learning part could come by remembering the decision tree routing - and remembering which recipes the use actually committs too - and why, and changing the decision weighting as a reaction

---

### Post by tjoff on 2012-01-16
I made a supplement to Tony Flury's post. The "ingredient substitution/omission problem" cannot be solved by a database search.

I warn you though. If you want to implement a solution based on machine learning, you must have proper training data. This might be a problem, unless you know some serious recipe data bases with user ratings, or unless you REALLY like to cook for your friends :)

Since you only have 2 months I would strongly recommend that you use some training data that already exists.

---

### Post by RobikShrestha on 2012-01-16
@[Tony Flury]("http://ubuntuforums.org/member.php?u=591713"): Thanks again! 

**So, this is what I understand from your reply:**

AI would be used to rank the best recipes by rating the recipes according to the number of times they are used?

**Quote from your reply:**

"The Learning part could come by remembering the decision tree routing -  and remembering which recipes the user actually commits too - **and why,**  and changing the decision weighting as a reaction"

**I am confused!**

I do not understand the "**and why**" part.
Did you mean we allow users to comment on recipes? But I could not possibly use that in the recipe search algorithm.

---

### Post by RobikShrestha on 2012-01-16
@[tjoff]("http://ubuntuforums.org/member.php?u=805999"): Thanks for the reply.
I am a little bit confused what the training data is used for. Are they used for ingredient substitution? Wouldn't such rules differ from one recipe to another?

---

### Post by tbastian on 2012-01-16
I think what they are getting at is that for a system to be considered "artificial intelligence" it needs to learn. It requires feedback from somewhere, in some form. They seem to be suggesting how you may want to do that.

An interesting feature for this sort of thing would be to keep track of what the user makes, and to suggest different recipes based on a balanced diet.

---

### Post by RobikShrestha on 2012-01-16
**May be I should keep things simple by including the following features only:**

1. Allow users to specify ingredients, time and skill level required to cook the food (may be the name of food he/she wants to eat eg: pizza, cake, ice-cream whatever)

2. Display search results based on the user's specifications

3. Allow users to rate recipes (this would affect the future search results)

**This is what I think should be the structure of the recipe:**

1. List of ingredients (each ingredient annotated with "optional", "compulsory", "alternative ingredients = another ingredients") (Used in searching)

2. Cooking time (eg: 1.5 hours to 2 hours) (Used in searching)

3. Steps involved (not used during searching)

Use of AI: To use ratings of recipes for displaying search results.

**Again the same question:**

How can I get more AI within this scope?

---

### Post by tjoff on 2012-01-16
@tbastian
Exactly, well put.

@RobikShrestha
Everything your computer can ever "know" about cooking, is what you tell it. This is "training data" in the context of Artificial intelligence. In the context of expert systems you would probably call it the "knowledge base". Computer programs cannot make good decisions without proper input data. 
"Wouldn't such rules differ from one recipe to another?"
Exactly. This is why it is a hard (and interesting) problem to solve. But if you knew the rules in beforehand, there would be no reason to use AI.

If your database already contains the answer to your specific question, it is a (possibly very hard) search problem.
If not it is a (possibly impossible) AI problem.

---

### Post by RobikShrestha on 2012-01-16
Thanks! Now I get it! 

May be the way I am thinking of the problem is interesting but not suitable for AI project. 
In fact there seem to be plenty of recipe generators allowing users to search for recipes using ingredients etc. May be I should do something else...

And about the ingredient substitution problem, I think I need to know a lot about cooking too. As a beginner, I have no idea what kind of training data should be used (to train the program so that in the future it can tell if an ingredient can be substituted by another in a particular dish). 

Should I give up and think about another topic?

---

### Post by Barrucadu on 2012-01-17
This thread inspired me to actually make an AI recipe generator ([https://github.com/Barrucadu/recipe](https://github.com/Barrucadu/recipe)).

Basically, I modelled ingredient compatibility as a totally-connected weighted graph. Each vertex in the graph is of the form *(CookingMethod, Ingredient)*, and the cost of each arc is the rating of that pair. When generating a recipe of *n* ingredients, it (non-deterministically) finds a maximal-cost *n*-length path in the graph, starting from some given vertex (the initial ingredient, which is totally random).

A recipe as a whole can be rated as good or bad. If it is rated as good, the rating of each pair of ingredients in the recipe is incremented, if bad it is decremented.

I'm hoping that, given sufficient time to train it, it will generate non-terrible recipes some day :)

---

### Post by RobikShrestha on 2012-01-17
Thanks for the link. I will read the comments in the code.

I am not experienced in AI, so I guess for the training data, we would require recipes converted into the form of weighted ingredient pairs so that the arcs in the graph gain appropriate weights.

---

### Post by RobikShrestha on 2012-01-17
I was thinking of adding a "START" node, so that the recipe does not start from inappropriate nodes.

Also,
  
[B]Cooking time and Quantity of ingredients:

[/B]It would be great to have these details, but I do not think I am gonna include them in the solution. 

However I would do it as follows:

May be the training data can provide those details for (1 person, 2 people and 4 people basis). Then, each time the graph is trained, the quantity of ingredients specified by the training data is added (i.e. for each node visited). Also the information on how many times the node was updated is also added.
 
Then, we can find average quantity by dividing the total quantity by the number of times the node was updated (this would be different for 1 person, 2 people and 4 people). Same would apply for the cooking time. May be it would still be inaccurate but it would at least provide some sort of estimate of how much and how long to cook.  

If anyone has a different idea on how to add these two features, please reply.

---

### Post by RobikShrestha on 2012-03-22
Here is the source code and database sql file:

[https://github.com/robikshrestha/Master-Recipe-Maker](https://github.com/robikshrestha/Master-Recipe-Maker)

---

