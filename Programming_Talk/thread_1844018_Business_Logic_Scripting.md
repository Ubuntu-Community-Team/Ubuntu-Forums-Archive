---
title: "Business Logic Scripting"
date: 2011-09-14
forum: Programming Talk
---

### Post by N1GHTS on 2011-09-14
I am designing a project geared towards business and is built in C  language. The design of the various interface screens are currently in  XML/CSS. The target platform is a PC running Ubuntu Server or Windows (depending on client needs). To  compile the software, I first run a source-to-source compiler which  converts the XML/CSS into C code, and then compiles that to the final  product. This source-to-source compiler was also designed by me and  written in C.

I am looking for a scripting language which could be embedded into the  source-to-source compiler that allows for the following things:

1. Code that is easy to read and write, even many years in the future,  that can be picked up by anyone and modified to change business policies  which in many cases would involve changes to the way the interface  works.

2. Easily embeddable into existing C code, allowing structures and  functions to be directly accessible from the scripting language.

3. Fast and relatively light weight, especially for our linux installations.

4. Ultra Stable. The software can not afford downtime whatsoever.

5. Can stand the test of time, to be around for decades. In other words,  this language should be backed by some kind of standard. It should also  not require frequent updates to bug fixes as that is not an easy option.

6. When we hire new programmers, we would recommend that they know this  scripting language prior to starting, so it should be relatively well  known.

One of my first choices was the Python language. While I have no experience in Python, I do know that it  is a well documented, popular, and embeddable scripting language used  for extensions, scripting and automation of software. What I don't know  if this is the best language for the job. My primary concern is building  complex business logic using this language.

Another consideration is using Lua, which I understand is simpler  syntactically and geared towards being embeddable in C. But I don't know  if it has any real advantage over Python for my implementation, and I  believe Python is far better positioned as far as documentation,  support, and training is concerned.

A final consideration is to use COBOL, a language built for business  logic and still one of the most widely used programming languages in the  world. While its not a scripting language in the same way Python or Lua  is, its time-tested stability and popularity could be to my advantage,  but I am not sure how I would go about embedding it to my compiler.  Also, if Python can compete with the buisness logic programming of  COBOL, I believe it would be advantageous to stick with something  mainstream.

With that said, I am eager to get your take on this subject

---

### Post by karlson on 2011-09-14
> **N1GHTS said:**
> I am designing a project geared towards business and is built in C  language. The design of the various interface screens are currently in  XML/CSS. The target platform is a PC running Ubuntu Server or Windows (depending on client needs). To  compile the software, I first run a source-to-source compiler which  converts the XML/CSS into C code, and then compiles that to the final  product. This source-to-source compiler was also designed by me and  written in C.

I am looking for a scripting language which could be embedded into the  source-to-source compiler that allows for the following things:


Before we get to any of the requirements I'd like to know what is the purpose of the scripting language in your case?  From what I understand you are taking XML/CSS and converting it to C where XML/CSS defines I am guessing business logic for you...

---

### Post by N1GHTS on 2011-09-14
XML is for the user interface and report structures, CSS applies design rules to display those structures. The languages inherently do not offer any logic whatsoever. 

Currently the logic that deals with these structures in relation to its application is written in a macro-intensive C, and I am trying to find a scripting language to do away with that unneeded complexity, especially since we plan to expand the use of this engine to many different implementations using the same core engine, as well as offer dynamic customisations for the client's ever changing policies.

---

### Post by CptPicard on 2011-09-14
Guile? Can't beat a lisp in the "test of time" department...

---

### Post by ofnuts on 2011-09-14
> **CptPicard said:**
> Guile? Can't beat a lisp in the "test of time" department...Anyone who can code decently in any Lisp derivative will not be looking for a job involving maintaining business applications. If you are looking for business applications programmers, use languages that BAPs are used to: Cobol, Java, C#, VisualBasic

---

### Post by N1GHTS on 2011-09-14
> **ofnuts said:**
> Anyone who can code decently in any Lisp derivative will not be looking for a job involving maintaining business applications. If you are looking for business applications programmers, use languages that BAPs are used to: Cobol, Java, C#, VisualBasic

That sounds logical to me. 

What is your opinion on BAP's and the Python language?

---

### Post by ofnuts on 2011-09-14
> **N1GHTS said:**
> That sounds logical to me. 

What is your opinion on BAP's and the Python language?Those I frequent are barely aware of its existence...

---

### Post by NathanB on 2011-09-14
It sounds like Lua meets most of those requirements:
[http://www.lua.org/about.html](http://www.lua.org/about.html)

---

### Post by N1GHTS on 2011-09-14
> **ofnuts said:**
> Those I frequent are barely aware of its existence...

That's a very useful insight. 

I have used C# for web programming and find its ability to guide complex business logic weak in the context I need it for. Specifically, C# is too structured, requiring the programmer to create a series of abstract objects and property handlers for complex policy situations. I don't like inconsistency and in my experience, each new policy is its own world and its own project.

Ideally the business policies should spell itself out within language context without having to build a house around each policy. My need for a readable language is not about control as much as it is  satisfying complex conditions. Furthermore, Some logic in our scripts are highly  recursive, requiring that the script revisit conditions that changed  depending on changes of status during procedural logic interpretation. And finally, the language I choose should be a secondary language that we use when we need it, rather than it being the dominant layer between the core system and the interface.

With that said, and given the close relationship between Java and C#, do you think COBOL would be any better?

---

### Post by N1GHTS on 2011-09-14
> **NathanB said:**
> It sounds like Lua meets most of those requirements:
[http://www.lua.org/about.html](http://www.lua.org/about.html)

I am definitely attracted to its philosophy of simple syntax and simple C integration, but ultimately the people who will work on these scripts will be business application programmers, and as "ofnuts" mentioned, they never heard of Lua or Python. On the other hand, we aren't particularly picky about who we will eventually hire to manage these changes, even if it means paying for some training. 

But the very biggest issue to me is readability.

Here is a pseudo code example of complex business policy that I would like to see a language translate well.

```

IF (EDITING OR INSERTING)
  ALSO IF (
     PERSONTYPE IS EMPLOYEE OR 
     (PERSONTYPE IS MANAGER AND STATUS IS LESS THAN 3)
  ) AND MODE IS COMMENTS_TABLE_MODIFIED
  WHEN LOAD OR ADMINISTRATION_STATUS_CHANGED THEN
    SHOW COMMENTS_TABLE;
    HIDE ADMINISTRATION_TABLE;
    CALL UPDATE_AUDITING_ROSTER;
END
IF VIEWING AND (PERSONTYPE IS EMPLOYEE OR GUEST)
  WHEN LOAD OR UPDATE_AUDITING_ROSTER THEN
    SET PROPERTYCOUNT TO DATABASE.MAIN_TABLE.PROPERTYCOUNT;
    SET PERSONNAME TO DATABASE.MAIN_TABLE.FULLNAME;
END

```So the question is, which language should I chose to easily describe this sort of quadratic logic in a way that can be revisited many years in the future without costing us time and money to relearn it and modify it.

---

### Post by llanitedave on 2011-09-14
Logic is logic, and language independent.  The business logic does not come from the programmer -- it's given TO the programmer to implement in code.  

You mentioned > 1. Code that is easy to read and write, even many years in the future, that can be picked up by anyone and modified to change business policies which in many cases would involve changes to the way the interface works.

This sounds like to me the logic would be modified by people who are not programmers.  In which case you need to keep scripts simple and straightforward.  I don't know lua, but of the other languages mentioned so far only Python has a reasonable chance of being understandable to hastily-trained application users.

Or you might consider a simple and limited templating language that's visible to the users, but backed up by whatever languages the application builders would choose to work in.

---

### Post by karlson on 2011-09-14
> **N1GHTS said:**
> That sounds logical to me. 

What is your opinion on BAP's and the Python language?

Outside of Financial Industry and Technology companies people don't seem to use it.  Most commonly it's regarded as a Linux/UNIX new scripting tool.

---

### Post by karlson on 2011-09-14
> **llanitedave said:**
> This sounds like to me the logic would be modified by people who are not programmers.  In which case you need to keep scripts simple and straightforward.  I don't know lua, but of the other languages mentioned so far only Python has a reasonable chance of being understandable to hastily-trained application users.

Somehow I doubt that a hastily trained User would be able to do the scripting in Python even remotely reasonably.

---

### Post by myrtle1908 on 2011-09-14
JavaScript?  Perhaps with your own tailored-subset of same?

[https://developer.mozilla.org/en/SpiderMonkey](https://developer.mozilla.org/en/SpiderMonkey)
[https://developer.mozilla.org/en/How_to_embed_the_JavaScript_engine](https://developer.mozilla.org/en/How_to_embed_the_JavaScript_engine)

---

### Post by N1GHTS on 2011-09-14
> **llanitedave said:**
> 
Or you might consider a simple and limited templating language that's visible to the users, but backed up by whatever languages the application builders would choose to work in.

May you suggest a simple and limited templating language?

A few years ago I created a very human readable scripting language which we code named "hyperscript" to provide buisness policy programming over the C# Dot Net framework, and it is currently being used by one of our clients, and works quite well. Unfortunately, it is not mature and has conceptual deficiencies that cause it to be limited and sometimes inefficient.

Since we plan on moving away from Dot Net, I would have to translate the parsing engine to work with this new system in C, and I would rather focus my energy on a more mature language if one exists to compete with our own "hyperscript" system.

---

### Post by karlson on 2011-09-14
> **N1GHTS said:**
> 
But the very biggest issue to me is readability.

Here is a pseudo code example of complex business policy that I would like to see a language translate well.

```

IF (EDITING OR INSERTING)
  ALSO IF (
     PERSONTYPE IS EMPLOYEE OR 
     (PERSONTYPE IS MANAGER AND STATUS IS LESS THAN 3)
  ) AND MODE IS COMMENTS_TABLE_MODIFIED
  WHEN LOAD OR ADMINISTRATION_STATUS_CHANGED THEN
    SHOW COMMENTS_TABLE;
    HIDE ADMINISTRATION_TABLE;
    CALL UPDATE_AUDITING_ROSTER;
END
IF VIEWING AND (PERSONTYPE IS EMPLOYEE OR GUEST)
  WHEN LOAD OR UPDATE_AUDITING_ROSTER THEN
    SET PROPERTYCOUNT TO DATABASE.MAIN_TABLE.PROPERTYCOUNT;
    SET PERSONNAME TO DATABASE.MAIN_TABLE.FULLNAME;
END

```So the question is, which language should I chose to easily describe this sort of quadratic logic in a way that can be revisited many years in the future without costing us time and money to relearn it and modify it.

I still don't see any reason not to use XML as long as you define the set of tags that you can use your logic above becomes an XML file below.

```

<if>
    <condition
        __name=EDITING
        __value=SET
    />
    <OR/>
    <condition
        __name=INSERTING
        __value=SET
    />
<then>
    <if>
        <condition
            __name=LOAD
            __value=SET
        />
        <or/>
        <condition
            __name=ADMINISTATION_STATUS_CHANGED
            __value=SET
        />
    <then>
        <if>
            <condition
                __name=PERSONTYPE
                __value=EMPLOYEE
            />
            <or/>
            <and>
                <condition
                    __name=PERSONTYPE
                    __value=MANAGER
                />
                <condition
                    __name=STATUS
                    __comparison=LT
                    __value=3
                />
            </and>
            <and/>
            <condition
                __name=MODE
                __value=COMMENTS_TABLE_MODIFIED
            />
        <then>
            <execute>SHOW COMMENTS_TABLE</execute>
            <execute>HIDE ADMINISTRATION_TABLE</execute>
            <execute>CALL UPDATE_AUDITING_ROSTER</execute>
        </if>
        <if>
            <if>
                <condition
                    __name=LOAD
                    __value=SET
                />
                <or/>
                <condition
                    __name=UPDATE_AUDITION_ROSTER
                    __value=SET
                />
            <then>
                <if>
                    <condition
                        __name=VIEWING
                        __value=SET
                    />
                    <and/>
                    <or>
                        <condition
                            __name=PERSONTYPE
                            __value=EMPLOYEE
                        />
                        <condition
                            __name=PERSONTYPE
                            __value=GUEST
                        />
                    </or>
                <then>
                    <execute>SET PROPERTYCOUNT TO DATABASE.MAIN_TABLE.PROPERTYCOUNT</execute>
                    <execute>SET PERSONNAME TO DATABASE.MAIN_TABLE.FULLNAME</execute>
                </if>
            </if>
        </if>
    </if>
</if>

```

Personally I don't think that you will have more then a dozen tags that you will be using.

Every application I have seen that implements a scripting language is implementing a custom one since you need to pass around not just what it is that you want the script to do but also the data that you want to do it to.  And you would have to hard define the correlation of the variable used in the script to the memory/variable used in the C code.

---

### Post by N1GHTS on 2011-09-14
> **myrtle1908 said:**
> JavaScript?  Perhaps with your own tailored-subset of same?

[https://developer.mozilla.org/en/SpiderMonkey](https://developer.mozilla.org/en/SpiderMonkey)
[https://developer.mozilla.org/en/How_to_embed_the_JavaScript_engine](https://developer.mozilla.org/en/How_to_embed_the_JavaScript_engine)

I have explored this option before, although came to no definite conclusions. How is Javascript a better scripting language than Python or Lua for business logic modelling?

---

### Post by N1GHTS on 2011-09-14
> **karlson said:**
> I still don't see any reason not to use XML as long as you define the set of tags that you can use your logic above becomes an XML file below.

Personally I don't think that you will have more then a dozen tags that you will be using.

Every application I have seen that implements a scripting language is implementing a custom one since you need to pass around not just what it is that you want the script to do but also the data that you want to do it to.  And you would have to hard define the correlation of the variable used in the script to the memory/variable used in the C code.

First of all, I appreciate your effort in answering my question.

Second, I agree with you about how the complex logic can be interpreted straight from XML, its a very interesting approach indeed.

Third, I also agree that no matter what language I choose for this job, it would have to be made to work custom to the engine it runs on, and at that point it is a custom language implementation. This is currently true of the CSS variant being used in the engine.

I guess the only issue I have with scripting procedural code in XML is that XML is not really designed to do that. Seems like a workaround, albeit a clever one, and a bit cluttered for my taste, yet either way I will keep that in mind.

---

### Post by slavik on 2011-09-14
language war commence?

Perl has an embeddable module. :)

---

### Post by N1GHTS on 2011-09-14
> **slavik said:**
> language war commence?

Perl has an embeddable module. :)

In a language war, the warrior should use more than one swing of his sword before expecting to win the battle. In other words, given that there are 6 points I outlined in my first message, your comment only satisfied one of those conditions.

Its nice to know that Perl is an embeddable language, but is it a good scripting language for complex business logic? And on your next swing tell me in what ways Perl is better suited than Python, Lua, or Cobol for those points outlined.

---

### Post by myrtle1908 on 2011-09-14
> **N1GHTS said:**
> I have explored this option before, although came to no definite conclusions. How is Javascript a better scripting language than Python or Lua for business logic modelling?

I would say it's neither better nor worse.  Either way you will be needing to extend the language to support your needs.  JavaScript is very easy to extend with its prototypical model.  For example:-

```
String.prototype.ucFirst = function() {
  var f = this.charAt(0).toUpperCase();
  return f + this.substr(1);
};
```

Now the String class (object) has a ucFirst method (function).

I recommended JavaScript as I thought perhaps you were running some browser engine (eg. WebKit) to render (or even run) your app.  I may have misread.

---

### Post by N1GHTS on 2011-09-15
> **myrtle1908 said:**
> I would say it's neither better nor worse.  Either way you will be needing to extend the language to support your needs.  JavaScript is very easy to extend with its prototypical model.  For example:-

```
String.prototype.ucFirst = function() {
  var f = this.charAt(0).toUpperCase();
  return f + this.substr(1);
};
```Now the String class (object) has a ucFirst method (function).

I recommended JavaScript as I thought perhaps you were running some browser engine (eg. WebKit) to render (or even run) your app.  I may have misread.

There is no web component or web anything in this system. Its runs in ANSI C, everything written from the ground up, including the display rendering engine which uses OpenGL acceleration. With this kind of control in our applications, we can do just about anything as far as embedding a new scripting language is concerned. 

So I don't need to conform to any language, this is completely a question of satisfying a few key points, with the most important point being that it has to be a friendly language to write complex business policy logic.

---

### Post by myrtle1908 on 2011-09-15
> **N1GHTS said:**
> There is no web component or web anything in this system. Its runs in ANSI C, everything written from the ground up, including the display rendering engine which uses OpenGL acceleration. With this kind of control in our applications, we can do just about anything as far as embedding a new scripting language is concerned. 

So I don't need to conform to any language, this is completely a question of satisfying a few key points, with the most important point being that it has to be a friendly language to write complex business policy logic.

Ah, I understand now.  You may struggle to find a specialised BL language to suit your needs, at least one which isn't tightly bound to its typical execution environment, database, stack etc.

Take Progress 4GL for example.  It is a BL only lang and tightly bound to its database.  A horrible beast it is, but works nicely (and only) within its bounds.

Why not invent your own grammar?  Is that feasible?

I have done something similar-*ish*, where instead of requiring our staff to write pure JavaScript (and having access to the full DOM etc), we expose only a few macro-like functions and other useful toys to them.  This enabled our non-tech staff to quickly build working systems which would otherwise have required a developer.

That said, I see that this [JavaScript - or a subset thereof] is not really what you are looking for ... you would end up with bracket-pollution and scripters would require at least some basic programming knowledge.

---

### Post by N1GHTS on 2011-09-15
> **myrtle1908 said:**
> Ah, I understand now.  You may struggle to find a specialised BL language to suit your needs, at least one which isn't tightly bound to its typical execution environment, database, stack etc.

Take Progress 4GL for example.  It is a BL only lang and tightly bound to its database.  A horrible beast it is, but works nicely (and only) within its bounds.

Why not invent your own grammar?  Is that feasible?

I have done something similar-*ish*, where instead of requiring our staff to write pure JavaScript (and having access to the full DOM etc), we expose only a few macro-like functions and other useful toys to them.  This enabled our non-tech staff to quickly build working systems which would otherwise have required a developer.

That said, I see that this [JavaScript - or a subset thereof] is not really what you are looking for ... you would end up with bracket-pollution and scripters would require at least some basic programming knowledge.

It's true that much of the policy logic is by nature tightly bound to data, and thus mostly resides in the database realm. These policy scripts I need to implement support for are interface specific, rather than database specific, so the number of control commands I need are few when compared to any general purpose scripting language.

It would seem that, from what I understand of my own situation so far given the responses, that there is no standard 4th generation programming/scripting language that would bend sufficiently to our business policy scripting needs that could do a better job than creating a custom parser from scratch with a custom language. 

Otherwise, I would have to support more language than I need for the kind of simple scripting required in our application, which essentially would butcher the language and end up making its "no learning curve" advantaged nullified by its forced specialized interpretation.

If I go the route of making my own interpreter for a new custom language, I should at least closely model it to some standard language, which would at the very least satisfy points 5 and 6.

I guess I could take a look at "Progress 4GL" and borrow some of its programming model.

On a final note, this result does not give me much satisfaction, but its logical.

---

### Post by myrtle1908 on 2011-09-15
> **N1GHTS said:**
> I guess I could take a look at "Progress 4GL" and borrow some of its programming model.

It's called Advanced Business Language now ... [http://en.wikipedia.org/wiki/OpenEdge_Advanced_Business_Language](http://en.wikipedia.org/wiki/OpenEdge_Advanced_Business_Language).  Personally I hate it - but some love it!

---

### Post by ofnuts on 2011-09-15
> **llanitedave said:**
> This sounds like to me the logic would be modified by people who are not programmers.This is the very worrisome part of the thing. Most people (and this includes the management) assume that the work of "programmers" is to write code. This is completely false. In business applications, the code writing part is 10% of the work (15% if you add the debugging). The time-consuming and difficult part is figuring out the real logic behind the specs, converting it into a computer-manageable logic (code, SQL tables, configuration files...) and finding out how to add it to the current scheme of things without breaking it. People who can do this correctly normally also know how to write code (and they also know how to manage sustainable development, with source repositories, debuggjng, testing...). So, in the end, the only people who can change the business logic are programmers, or have the skills to be so.

---

### Post by slavik on 2011-09-15
> **N1GHTS said:**
> In a language war, the warrior should use more than one swing of his sword before expecting to win the battle. In other words, given that there are 6 points I outlined in my first message, your comment only satisfied one of those conditions.

Its nice to know that Perl is an embeddable language, but is it a good scripting language for complex business logic? And on your next swing tell me in what ways Perl is better suited than Python, Lua, or Cobol for those points outlined.
Cobol ... unless you bring people out of retirement and pay them large sums of money like the State of California, don't pick it.

Lua ... AFAIK, this language was made to be embeddable. WoW exposes and API within Lua for all Addons. Problem is, this is not a wide spread language.

Python ... indentation matters, This could be an issue with hardcoded routines and users attempting to augment your program.

Now, point by point ... (making me do work :():
1. The only language that can fit this is BASIC or some language you would have to invent.
2. Perl and Lua are easy embed, Python, I do not.
3. This is kind of a loaded point. How fast? Perl is not "SLOW" but it is not as fast as well optimized code. It is small but can be augmented by Perl modules. cpan.org is the official Perl module repository.
4. Perl has existed for a very long time. Although C is still the oldest language that is in wide use today. C was created in the early 70s. Perl first came around in 1987.
5. AFAIK, Javascript is the only scripting type language to have some kind of a standard (ECMA).
6. Anyone who wants to do System Administration work on UNIX systems would most likely know Perl as Perl is the most used language for System Administration.

With that said, there is no silver bullet. :)

---

### Post by karlson on 2011-09-15
> **slavik said:**
> 
Now, point by point ... (making me do work :():

Your avatar would be rather upset with you.
> 
1. The only language that can fit this is BASIC or some language you would have to invent.
2. Perl and Lua are easy embed, Python, I do not.

I still have a concern that no matter how you slice it you would need to have some what of passing the variables from you overall system up to the script, I haven't seen how Lua does that but most software developers writing business apps aren't in the know of how to do that.
[http://www.ibm.com/developerworks/linux/tutorials/l-perlscript/l-perlscript-pdf.pdf](http://www.ibm.com/developerworks/linux/tutorials/l-perlscript/l-perlscript-pdf.pdf)
> 
3. This is kind of a loaded point. How fast? Perl is not "SLOW" but it is not as fast as well optimized code. It is small but can be augmented by Perl modules. cpan.org is the official Perl module repository.

No matter how you slice it adding a level of indirection will be slower then running straight up machine code, how slow will require testing.
> 
4. Perl has existed for a very long time. Although C is still the oldest language that is in wide use today. C was created in the early 70s. Perl first came around in 1987.

Python has been around for about 20 years too.

> 
6. Anyone who wants to do System Administration work on UNIX systems would most likely know Perl as Perl is the most used language for System Administration.

With that said, there is no silver bullet. :)

I would suggest to point 6 the modern guys would know both Perl and Python, however, there are fewer and fewer of those people.  System Administration is becoming more and more commoditized, so larger companies might have 2-3 engineers that are able to program in either language and the rest simply use the scripts that these guys create.

I would still consider the implementation detail of passing data from the C program up to whatever script language chosen.  If all your scripts will be self contained and not taking anything from or passing anything down to the system then fork->exec and don't bother picking the scripting language.  The person implementing the business logic will choose that for you.

---

### Post by llanitedave on 2011-09-15
> **karlson said:**
> Somehow I doubt that a hastily trained User would be able to do the scripting in Python even remotely reasonably.

You're probably right.  Which is why I suggested the templating language kind of at the end of the thought process.  

And I don't have any suggestions for a particular templating language, you'd pretty much have to do one that's matched to the application you're building, I suspect.

Python, BASIC, Javascript, or some other imperative instruction set might work as the foundation for such a language, with maybe specific command and data choices available through pull-down menus or choice boxes.

I'm just thinking out loud here, but the point is you can allow a lot of user-control over functionality and appearance while still retaining the integrity of your foundational design.

Blender, Open Office, and the Gimp are three applications that allow for scripting with Python, but we don't consider that it would be done by a "typical" user.  Part of what you need to decide is what kind of user are you going to trust with these types of custom changes.  Anyone and everyone?  Then you're better off with a simple template language, or a glorified "Preferences" module.  Just those who know what they're doing?  Then Javascript and Python are both good choices, among others

---

### Post by llanitedave on 2011-09-15
> **N1GHTS said:**
> 
A few years ago I created a very human readable scripting language which we code named "hyperscript" to provide buisness policy programming over the C# Dot Net framework, and it is currently being used by one of our clients, and works quite well. Unfortunately, it is not mature and has conceptual deficiencies that cause it to be limited and sometimes inefficient.


Sounds like a perfect description of the scripting language that Apple created to run its Hypercard application in the 80's!  It had the same name, too.  :D

---

### Post by zkissane on 2011-09-16
XSLT.

If you're used to traditional programming languages, it's going to be very different for you.  Prepare for a learning curve.  But, if I understand you correctly, I think this is right up your alley.  In fact, if you do it right, the XSL stylesheet could entirely replace your "source to source" compiler.

An XSL stylesheet is a set of rules for transforming an XML document.  Usually, this is done to transform an XML document into another form of XML (such as converting an XML dataset into HTML for display in a browser), but there's no rule that says the output of a stylesheet has to be XML.  You could very easily write an XSL sheet to transform your own XML into C (assuming your XML schema is well suited for this, which it sounds like it is).

A potentially tricky part would be incorporating the CSS into the process.  In XSL, you have an engine (very similar in function to a compiler) and you give it an XSL stylesheet and the XML document to be transformed.  It outputs the results.  I don't really know if there's a way to "mix in" the CSS.

Anyway, there are several open source XSLT engines.  Most are Java or C/C++.  Good luck.

EDIT:  To clarify, you wouldn't embed XSLT as this hypothetical scripting language you want to develop.  You would simply design/agree on a way to express your business rules in XML and let the stylesheet rules grind out the C.  I think you could even separate the business rules from the interface screen designs, which would be a major maintenance improvement.

---

### Post by N1GHTS on 2011-09-17
Thank you for all your responses. I have read them all and it has contributed to my decision.

I have decided to expand upon the business language I mentioned code named "Hyperscript" since it is very similar to the business logic languages described here and since it is already being implemented in other products of our company.

My goal will be to model this language closely to other BAP languages, but tailored to work with our specific software. While its not what I originally wanted, the benefit of consistency outweighs the cost of time implementing and converting code between languages, at least for the time being.

Again, thank you all for your help.

---

### Post by llanitedave on 2011-09-17
Good luck, N1ghts.  Sounds like an interesting project, and I wish you success with it.  I think you probably have made the right choice.

---

