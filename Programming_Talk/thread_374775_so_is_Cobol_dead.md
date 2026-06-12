---
title: "so is Cobol dead?"
date: 2007-03-02
forum: Programming Talk
---

### Post by billdotson on 2007-03-02
I have heard of Cobol from my Dad saying he used to program in Cobol and recently I read that Cobol is one of those end of the line languages that is dead with no descendants.  Is this true?

---

### Post by yabbadabbadont on 2007-03-02
There are a lot of business applications still being used that are written in cobol.  I don't know how much new development is done using it, but there is a pretty large base of cobol software that is still maintained.  (usually on mainframes)  Dibol is a slightly newer language that uses a cobol like syntax (it also has some BASIC and Fortran elements in it)

---

### Post by pmasiar on 2007-03-02
> **billdotson said:**
> I have heard of Cobol from my Dad saying he used to program in Cobol and recently I read that Cobol is one of those end of the line languages that is dead with no descendants.  Is this true?

It is not dead yet - it is still breathing, but almost no pulse or reflexes :-)

Check [http://en.wikipedia.org/wiki/Cobol](http://en.wikipedia.org/wiki/Cobol) - external links at the end. Cobol is still used in big companies running big iron, and they still add new layers on top - but most Cobol experts are in their 50s and will not last forever. And new guys are nobody's fools: they do not want to waste years to master technology which is so obsolete and will not enhance their career options. Not many startups are using Cobol and hoping to get rich quick! 

Most companies using Cobol  wants to switch away from Cobol on first occasion but many cannot because of prohibitive cost - so they just drift around hoping someone will force them to switch.

Descendants: hell no we are moving away from all Cobol misfeatures. Worst offense was idea that more wordy code will make code self-documenting.

MULTIPLY 4 BY A GIVING C.
SUBTRACT C FROM B GIVING RESULT-1.

How much you will demand per hour to maintain shitty code like this?

---

### Post by yaaarrrgg on 2007-03-03
What's interesting is that SQL is very popular at the moment, and very cobol-esque.  SQL tries to make the machine speak natural language, so that assigning tasks are very much like speaking to the computer..  What's odd is that SQL has escaped a lot of criticism that has been directed at COBOL...

My father used COBOL: too... he saw it as agod send since before that (late 60's) he was programming everything in assembly.  Really, from that perpective, COBOL makes a lot of sense... it's the polar opposite of assembly, verbosely explicit (and is somewhat assebly-like in some approaches...for example the working storage section ).  Although nowadays, I think that context is lost ...  programmers are no longer trying to escape assebly, but rather "verbose" languages at the momebt.

I think what is popular is really a function of what progtrammers are trying to escape... and sometimes this changes.  Often the refuge becomes the new prison :)

Languages like C howevre I think found the happy medium between the cryptic and fast assembly syntaxes, and the natural langauge verbosity of cobol.  Basic is somewhere closer to cobol, and also not as popular anymore either.  I think that COBOL, or the basic concept, does have decendants though... LINGO is one based on the same concept: creating a natural language interface for the computer.

---

### Post by rplantz on 2007-03-03
> **pmasiar said:**
> 
Descendants: hell no we are moving away from all Cobol misfeatures. Worst offense was idea that more wordy code will make code self-documenting.

MULTIPLY 4 BY A GIVING C.
SUBTRACT C FROM B GIVING RESULT-1.

How much you will demand per hour to maintain shitty code like this?

I have had to maintain a lot of assembly language code that had no comments. And as a CS professor for a couple of decades, I had to read lots of C/C++ code that used non-descriptive variable names and had no comments. I have met programmers who thought it was cool to obscure the intent of their code. Some think of it as "job security."

I've never written nor maintained a COBOL program, but at least a little self documentation can make it easier to maintain code. 

I'm convinced that Kernighan and Ritchie did not know how to type. :)

---

### Post by Tomosaur on 2007-03-03
> **yaaarrrgg said:**
> What's interesting is that SQL is very popular at the moment, and very cobol-esque.  SQL tries to make the machine speak natural language, so that assigning tasks are very much like speaking to the computer..  What's odd is that SQL has escaped a lot of criticism that has been directed at COBOL...


Ah, but SQL was developed directly as a result of Cobb's specification for relational databases. SQL is not intended to manipulate data and provide functionality - it is more like a communication protocol - and it does its job very well for the most part. Natural languages do not translate well into instructions which need to be maintained and implemented on different platforms. Protocols, on the other hand - benefit greatly from natural language approaches. The purpose of 'select', for example, is obvious, as is 'update' and 'insert' - because they are all used in the same context, on the same data structures. A communication protocol can afford to be 'natural', because the implementation of each command achieves the same result on most platforms. If you introduce natural language to the actual programming language, it becomes very difficult to understand and maintain. 'Select' on a database obviously means 'Get this data' - whereas if you use 'Select' as an instruction in a language - the meaning of the command can vary too much based on context, because there are just too many possible data structures, types etc etc. It will mean 'more or less' the same thing, but 'more or less' is just not good enough.

---

### Post by pmasiar on 2007-03-03
> **yaaarrrgg said:**
> I think that COBOL, or the basic concept, does have decendants though... LINGO is one based on the same concept: creating a natural language interface for the computer.

which one of many [lingo]("http://en.wikipedia.org/wiki/Lingo_programming_language")s do you mean? wikipedia says there are at least 4 different languages called lingo - looks like none of them is a keeper :-) 

There is very big theoretical difference between natural languages (which are context-sensitive) and programming languages, which are context-free so we can create a parser for them. See [Chomsky hierarchy]("http://en.wikipedia.org/wiki/Chomsky_hierarchy"). And this it reason why we most likely never will program in natural language - it is difference like between 2D and 3D. A major breakthrough is required, couple of Nobel prizes, so don't hold your breath :-) Mind you these are not practical obstacles which can be overcame by focused hard work - these are major theoretical differences.

> **yaaarrrgg said:**
> What's interesting is that SQL is very popular at the moment, and very cobol-esque.  SQL tries to make the machine speak natural language, so that assigning tasks are very much like speaking to the computer..  What's odd is that SQL has escaped a lot of criticism that has been directed at COBOL...

> **Tomosaur said:**
> Ah, but SQL was developed directly as a result of Cobb's specification for relational databases. SQL is not intended to manipulate data and provide functionality 

I agree with Tomosaur. SQL is highly specialized [domain specific language]("http://en.wikipedia.org/wiki/Domain-specific_programming_language") with no pretensions being universal language like C, Python, Java, Lisp. And it is not verbose - in fact, has very limited vocabulary and very plain syntax, which happens to be English-like. But even is SQL, numerical operation use algebraic syntax and not English abomination used by Cobol.

> **yaaarrrgg said:**
> ... programmers are no longer trying to escape assembly, but rather "verbose" languages.

I think what is popular is really a function of what programmers are trying to escape... and sometimes this changes.  

Once problem is solved, new problems arise farther ahead, on higher level of abstraction. First it was discussion if wasteful spending of precious CPU resources by using "high level languages" is warranted -- oldtimers proposed to stick with assembler. I remember discussion about relational databases - implementation of relational operation is more wasteful than (now obsolete) hierarchical and network model databases. Nowadays, you will have hard time finding non-relational database, unless it is object database - a layer of abstraction above plain relational databases. As CPU cycles became cheaper, more and more work done before by programmers is pushed to CPU.

---

### Post by yaaarrrgg on 2007-03-03
> **pmasiar said:**
> which one of many [lingo]("http://en.wikipedia.org/wiki/Lingo_programming_language")s do you mean? wikipedia says there are at least 4 different languages called lingo - looks like none of them is a keeper :-) 

The early one from Macromedia (for Director) is what I'm talking about ...although  now they've retrofitted it with a syntax more like javascript (so it's not as painfull),.  Of course, I don't know that Lingo was inspired from COBOL, or merely history repeating itself (like two people making the same mistake) :)

> **pmasiar said:**
> I agree with Tomosaur. SQL is highly specialized [domain specific language]("http://en.wikipedia.org/wiki/Domain-specific_programming_language") with no pretensions being universal language like C, Python, Java, Lisp. And it is not verbose - in fact, has very limited vocabulary and very plain syntax, which happens to be English-like. But even is SQL, numerical operation use algebraic syntax and not English abomination used by Cobol.

Yes, that's a good point... SQL is perhaps a bad example, as it's domain specific.  IMO though as SQL has become more popular, it's being used more as a programming language (especially with stored procedures) . As more "business logic" is pushed into the backend, it becomes painfully verbose, even worse than COBOL.  For example:  

[http://99-bottles-of-beer.net/language-mysql-1252.html](http://99-bottles-of-beer.net/language-mysql-1252.html) (MySQL)
[http://99-bottles-of-beer.net/language-cobol-908.html](http://99-bottles-of-beer.net/language-cobol-908.html)     (modern COBOL)

:)

---

### Post by pmasiar on 2007-03-04
> **yaaarrrgg said:**
> Of course, I don't know that Lingo was inspired from COBOL, or merely history repeating itself (like two people making the same mistake) :) 

Regardless, Chomsky hierarchy either one is the same (context free), and as the article explains, principal difficulties are between the levels - to get to context-sensitive. Same difference :-)

>  as SQL has become more popular, it's being used more as a programming language (especially with stored procedures) . As more "business logic" is pushed into the backend, it becomes painfully verbose, even worse than COBOL.  :)

more business logic - less domain-specific, more like general programming language - added PL/SQL, which is completely different programming language based on [PL/1]("http://en.wikipedia.org/wiki/Pl/1"), added features and lost the simplicity. bad trade.

IMHO the best SQL-like language for databases was [PROGRESS 4GL]("http://en.wikipedia.org/wiki/Progress_4GL") it was high level language like PL/1, Pascal or what you have (later even OO) with integrated database access and GUI statements. Very efficient for app development. Bad marketing killed it.

---

### Post by _Agrajag_ on 2007-04-29
> **pmasiar said:**
> It is not dead yet - it is still breathing, but almost no pulse or reflexes :-)

Check [http://en.wikipedia.org/wiki/Cobol](http://en.wikipedia.org/wiki/Cobol) - external links at the end. Cobol is still used in big companies running big iron, and they still add new layers on top - but most Cobol experts are in their 50s and will not last forever. And new guys are nobody's fools: they do not want to waste years to master technology which is so obsolete and will not enhance their career options. Not many startups are using Cobol and hoping to get rich quick! 

Most companies using Cobol  wants to switch away from Cobol on first occasion but many cannot because of prohibitive cost - so they just drift around hoping someone will force them to switch.

Descendants: hell no we are moving away from all Cobol misfeatures. Worst offense was idea that more wordy code will make code self-documenting.

MULTIPLY 4 BY A GIVING C.
SUBTRACT C FROM B GIVING RESULT-1.

How much you will demand per hour to maintain shitty code like this?

First of all, it does tend to be easier to read than some languages, the example you chose is just not as ideal...  

MULTIPLY SUBTOTAL BY TAX GIVING TOTAL.

This is much easier to read than the example you gave above.  In the shops that I have worked in, for maintenance reasons descriptive variable names are required.  In this example subtotal, tax, and total would be defined in the working storage section...  and I make a fair amount of money maintaining COBOL programs. :)

---

### Post by Browser_ice on 2007-04-29
It's not that COBOL is dead, it simply isn't shown in schools anymore. Well at least where I live. I'm in Montreal, Canada and they stopped teaching Cobol since about 1990. But it is still widly used in banking institutions and goverment related big companies.

Doing COBOL alone is kind of rare now. It is usualy COBOL IMS or COBOL CICS.

---

### Post by g8m on 2007-04-30
I learned to program Cobol in the 90's. It's been 15 years or so I last saw a cobol source. It would not have been my choice. Cobol is almost readable for untrusting imbicils like those that work for banks and governments. 

Because programming is expensive and takes a lot of time, it's all about standard software solutions for entire software needs. ERP,  CRM, Data-warehousing, Applications. No more scribbling sources, that's done in third-world countries. Programming a dieing trade. It's all about managing and configuring now.

---

### Post by samjh on 2007-04-30
COBOL is far from dead.

There are still a lot of new projects using COBOL, usually for very large scale data crunching.  I don't mean your average company with clients in the tens or hundreds of thousands, but organisations like governments with tens or hundreds of millions of clients.

For example, the Australian Tax Office is still a very active user of COBOL; in fact, they assess COBOL as the only suitable language for the type of data crunching they need to do.  Australian government agencies are not shy about doing high-stakes projects using risky technologies (like the near-disastrous overhaul of the Australian Customs Service using web apps), so seeing the ATO still sticking to COBOL is quite remarkable.

COBOL's self-documenting style is nice, but they went a bit too far, IMHO. ;)  Still, I prefer verbose-and-readable languages to terse-and-undecipherable ones.

---

### Post by PSteiner on 2007-12-13
My experience with cobol covers 22 years, I am under 50. Is cobol dead? 

Well that depends on the perception and the quality of the programs already written and the custoimers need (which has been covered already).

I program in C/C++/V-C, V-Basic, Clarion 4th GL, SQL, Cobol, unix scripting, dos/windows scripting.  All these languages will get the job done if the language has the tools to communicate with hardware and user output is sufficient. In addition the quality of code, poor quality kills an application and confuses new progrmamers on the scene. I have seen horrible code in many languages and you can get a bad taste and blame the language,but really it is the author of the code who needs to be taken to task.

Having said thus, structured programming, consistant desciptive naming and libraries which allow the reuse of code in any language is key to on-going developemnt of an application, regardless of it's language. Newbies can pick it up and run with it add some training on the nuances of the application and they are ready to roll.

Cobol has all these abilities. The editor used is important to coding.  Cobol like all these other languages is stable.

Check out [http://www.liant.us/rm-cobol/rm-cobol-overview.html](http://www.liant.us/rm-cobol/rm-cobol-overview.html) for the latest on cobol. Liant used a slogan years ago when Windows started to take off  (graphical GUI with C and Basic) which cobol could not do. Liant came up with the slogan "Yes you can teach an old dog new tricks" and addressed the graphical interface.

I recently developed an added extension to do driect-depoist in our payroll package under cobol both cobol-74 and cobol 85. I print color laser invoices and post them to an SQL database for searching and viewing, emailing and faxing.  The quality of code in this application is exceptional and uses copy books (libraries) which helps in creating fresh applications. Nothing worse then duplicating your code throughout an application.

Cobol for me is not dead but offers another option and allows my customer to not have to re-invest in foundation to move forward in technology.

Lastly a more updated method to calculate in Cobol is to use the function compute.

Compute My-Gross Rounded =   My-Rate * My-Hours
          on size error move 9999999.99 to My-Gross.

Compute My-Gross Rounded =   My-Rate * My-Hours  on size error move 9999999.99 to My-Gross.

Notice the statements above, the first is broken into two parts via newline and indented. This allows the coder to focus on protions of the code visually. The second statement flows together and the coder must separate the statment mentaly. This takes the coder off his game because the structure does not help.

Notice no round type rquired? It rounds to the nearest decimal place that is defined in the My-Gross variable.

Bottom line is speed and quality in coding helps applications to stick around. The language needs to help the coder to follow good structure, consistant practices and satisfy the users desires. If a language can do that it is worth keeping around. When an application is developed it must be timely and virtually bug free. If the langauge cannot help the coder to do this then it is time to bury it.

HTH,
Peter

---

### Post by pmasiar on 2007-12-13
You proved my point (that COBOL is obsolete) pretty nicely.
Error handling in every statement? Having "compute" before every assignment? But then why it is "move 999 to my-var" instead of "my-var = 999", like compute statement does? Verbosity is as bad as terseness: succint is the right ballance.

I am happy for you that knowledge of COBOL keeps you employed (better you than me :-) ), and after you retire (or even before) maintenance of old obsolete apps might be outsourced/outshored to cheaper countries, so it might be cost-effective for some more time. 

But COBOL is obviously language well past prime time, as measured in **new** projects and companies started with Cobol as target language - and it is for the better, IMHO.

---

### Post by PSteiner on 2007-12-15
Obviously a hidden agenda, info to argue with dad, why not just ask for information about that, instead of masking your underlying agenda? 

Your example doesn't prove anything at all :), except you may not like to type. And it also makes me speculate whether you can read code at all.

My example of compute was to show clarity and some extra things you can do. The previous examples of multiply were terse enough, besides if you could or took the time to  read code then you would see that I am not initializing a field but calculating a value and initializiing at the same time.

Move zeros to my-var or move 0 to my-var would initialize the field, but you don't like typing "move". You'd rrather type My-Var=0. I get it, the statements in some instances seem unneccessary, unless your reading code. 

You asked as if you were curious about it. Instead you've already formed an opinion and if you want to pick it (cobol) apart then you may as well.  Then you crtique me and imply that I'm costing my client money?

You are so wrong here, good written code is good readable code which allows for faster maintenance and less bugs, as does good structure. Terse as in "texting" is fine as long as the code is clear in how it is written to others, yes you can abriviate variables and such to the point of uselessness.

Cobol does not insure good code or good structure, but it helps the programmer who wants to be clear about what thev'e coded and helps the programmer to eliminate bugs by carelessness and sloppyness. I have seen awful cobol code that just should be trashed  useless and costly. 

I can pick any of the languages apart, they are all not perfect. An earlier post said it isn't taught in schools any longer and nothing is more irritaing then ignorance masked with supposed knoweldge and little or not experience.

All languages have good and bad.

Nothing worse or costly in time then reading/writing sloppy terse code, that was written for job security. 

I realize that your opnion is already formed and nothing I can type will penetrate your pre-conceived notions.
 
Go ahead and believe what you want to believe - don't waste my time.

~Peter

---

### Post by Klipt on 2007-12-15
> **pmasiar said:**
> It is not dead yet - it is still breathing, but almost no pulse or reflexes :-)

But every time it has a stroke or heart attack, the banks rush it into I.C.U. :)

Even if Cobol seemed like a good idea at the time, I think it (and many better languages) will die simply because even better ones are being made available. Why try to bolt object orientation onto Cobol when you can use a real OO language?

> **pmasiar said:**
> There is very big theoretical difference between natural languages (which are context-sensitive) and programming languages, which are context-free so we can create a parser for them.

Unfortunately C++ [is](http://en.wikipedia.org/wiki/C%2B%2B#Parsing_and_processing_C.2B.2B_source_code) [not](http://books.google.com/books?id=XtM3aQ-E9NoC&pg=PA344&lpg=PA344&dq=c%2B%2B+context+free&source=web&ots=yEUFnzDNu2&sig=sAkkSxJUbLqOF9fwLsCrsecOqKY) [context free](http://eli.thegreenplace.net/2007/11/24/the-context-sensitivity-of-cs-grammar/), although it is close.

---

### Post by Martin Witte on 2007-12-15
> **g8m said:**
> I learned to program Cobol in the 90's. It's been 15 years or so I last saw a cobol source. It would not have been my choice. Cobol is almost readable for untrusting imbicils like those that work for banks and governments. 

Because programming is expensive and takes a lot of time, it's all about standard software solutions for entire software needs. ERP,  CRM, Data-warehousing, Applications. No more scribbling sources, that's done in third-world countries. Programming a dieing trade. It's all about managing and configuring now.

thank you! (a former civil servant now working for a bank as a programmer in your own country:))

---

### Post by LaRoza on 2007-12-15
There is a new OO Cobol: ADD 1 TO COBOL GIVING COBOL

Seriously, Cobol has its uses, but it is obviously not a general purpose programming language.

I imagine only a few members of this forum actually work in a field where it is useful, PSteiner seems to be one. Otherwise, it seems to have little use.

I doubt anyone would when confronted with a problem would whip up a COBOL program to solve it.

@PSteiner Is COBOL used much for non business/bank apps? Are there FOSS apps written in it? I know COBOL was intended for business type programming, and it would be interesting to see other apps that exist that are written in it.

---

### Post by Majorix on 2007-12-15
> so is Cobol dead?

Since I have never felt the use for it, it must be dead :D

---

### Post by pmasiar on 2007-12-18
[http://en.wikipedia.org/wiki/Dijkstra](http://en.wikipedia.org/wiki/Dijkstra) says in [How do we tell truths that might hurt?](http://www.cs.utexas.edu/~EWD/transcriptions/EWD04xx/EWD498.html): "The use of COBOL cripples the mind; its teaching should, therefore, be regarded as a criminal offence."

He is not excited about the BASIC either: "It is practically impossible to teach good programming to students that have had a prior exposure to BASIC: as potential programmers they are mentally mutilated beyond hope of regeneration."

:-)

---

### Post by Sporkman on 2007-12-20
> **pmasiar said:**
> 
MULTIPLY 4 BY A GIVING C.
SUBTRACT C FROM B GIVING RESULT-1.

How much you will demand per hour to maintain shitty code like this?

:lol:

---

### Post by guilly on 2007-12-20
I was taught cobol in College this year and glad i learned it because that is what got me a job this summer and a coop placement this term. So regarding the previous post from the guy in Montreal they are still teaching Cobol in Ontario!!!

---

