---
title: "Structuring unit tests - Advice needed"
date: 2010-04-08
forum: Programming Talk
---

### Post by pholding on 2010-04-08
I'm looking for some advice/recommendations on how I should structure a suite of unit tests for a project I've been working on. The code is written in C++ and uses exceptions rather than return codes. [COLOR=black][FONT=Verdana]Essentially [/FONT][/COLOR]the code is a wrapper around a C database library. The unit test framework will be Boost.Test. In the future the code will grow into a full application, but I'm taking small steps at the moment.
 
As I'm new to unit testing I'm unsure the tests should be structured and am keen to follow good practice.
 
I'm thinking of structuring the unit tests as follows
[LIST]
[*]Unit test 1 - connect to database
[*]Unit test 2 - create table
[*]Unit test 3 - insert record into table
[*]Unit test 4 - select record from table
[*]Unit test 5 - (perform some other SQL statements)
[*]Unit test 6 - disconnect from database
[/LIST]Some of these tests could be considered as setup and teardown code, but I want the unit tests to cover all code in my wrapper.
 
What I'm unsure about is whether it's considered good practice for one unit test to depend upon a previous unit test creating something in order to allow the test to be performed. 
 
The other issue I've got is whilst the function may not have thrown an exception it doesn't necessary mean the function did what its supposed to do. For example unit test 2 might not throw an error, but the only way I'll know if the function worked correctly is to query the database metadata or do unit test 3. Should unit test 2 only check that an error was not thrown or should it also call another function to query the metadata and then check the result of that function before marking unit test 2 as a success?
 
I've hunted on Google and whilst I can find lots of information about how to code unit tests with various frameworks, I haven't found much on the structure and granularity of unit testing.

---

### Post by theDaveTheRave on 2010-04-08
pholding,

This seems to me like an excelent question.

It is something I never really contemplated much before, as the method I use for development follows the following structure....

write stand alone code and test functionality by changing code and adding different instructions. For when I wanted to access a DB I simply designed a number of scripts to use various class files (i develop in java mostly)

so in essence:
class to create (and hold) a connection to the database
class to determine access rights (user name / pwd)
class to send queries to DB
class to receive queries from DB and display them to user


Each class is so small in on it's own that testing the functionality as I build the system is 'fairly easy'.

It was then just a matter of making the code take user input variables rather that fixed input for the actions.

These user input variables where demanded from the user at the CLI (no gui involved at this point).

I could then confirm that this all worked out OK by putting in queries and double checking the DB directly (or programatically).

It was kind of a test as you make type method. possibly not very practical but with the use of 'object oriented' methodology this should also be possible for your situation (I know that I used the same idea when I occasionally developed in C).

like you however I don't know how good this is as a method of 'testing' my code. All I know is that the code does what I want it to, and shouldn't have any 'undesired' action as each class is so small.

How this will work out when I start designing the GUI front end will need to be seen however.

I am also interested in the answers you get to this question.

David

---

### Post by Some Penguin on 2010-04-08
I would consider connecting and disconnecting to be prerequisites, not actual tests; they are required for pretty much any database operation, and they are probably the least likely bits to fail, and aren't especially useful unless something else does work.

---

### Post by tgalati4 on 2010-04-08
Or, make one unit test that performs all of those functions.  I'm not sure of the benefit of making your test atoms that small.  After all, when you make changes to your application, then run the unit test, you want to be able to perform all of those functions without regression.

More important is to include some profiling--how much time it takes to perform each of those operations.  Many performance regressions are subtle when your application grows.  If you keep a log of those test results over time, you can see where your biggest performance hits are.  Then you can focus your performance improvements on those modules that are taking the most wall-clock time.  

You don't want your users waiting too long for basic queries or table updates.

The open source customer relations management (CRM) tool [http://sugarcrm.com](http://sugarcrm.com) contains a timekeeping module that displays the wall-clock seconds at the bottom of each retrieval page.  You can turn that off, but it's helpful to see how fast the application (mainly PHP/HTML pages with mysql) runs on different servers and with different tweaks to the PHP code.  Slow pages can get extra attention.  Also, you can use it as a gauge as to when to run some mysql house-cleaning, table-trimming, etc.

Another aspect to consider is stress-testing.  Unit testing is good for rollout testing.  You've made a few tweaks to the application and you want to deploy it--so run your unit test to make sure it doesn't blow up right away.  Many issues crop up with edge cases:  When databases grow large, PHP requests grow beyond what you set your php.ini to handle, many users pounding the database at once, many table inputs simultaneously, etc.

Your unit testing should include some stress tests that handle reasonable edge cases--max number of expected users, maximum number of fields in the database, maximum number of tables to hold, maximum number of simultaneous page requests, etc.

I wrote a mapping application that used an USB GPS dongle.  I wanted to see how robust the gpsd server was.  I ran 7 instances of my program each trying to grab data from the same gps device.  Processes/threads grew to 400.  When I started the 8th instance, processes shot up to 4,000 and the system effectively froze.  I was able to run 7 instances for 48 hours straight with logging, and graphical map updates, with no memory leaks and close to 100% CPU load.  Needless to say, one instance of this app was pretty robust for a field application.

---

### Post by diesch on 2010-04-08
I think writing tests for connecting and disconnecting is still useful to check the function of parameters (if there are any) and to make sure they fail in the right way if something is wrong. 

Making connecting and disconnecting prerequisites makes it easier to test how other functions behave if they are called after a failed connect, without a connect or after a disconnect.

---

### Post by pholding on 2010-04-09
Just wondering whether any other C++ developers on this forum have use a unit testing framework for their projects and if so how they deal with the issues I've encountered.
 
In the past I've just written a simple bit of code to call all of the functions passing in the relevent data and write the output to the console, however as the code base grows this doesn't seem a very scalable solution.

---

### Post by diesch on 2010-04-09
I'm a python programmer but I guess the issues aren't that different there.

If your test suite grows or contains some time consuming tests it's important to have a testing framework that allows you to run only specific tests or group of tests so that you don't need to wait for all the tests to finish but can just run the ones that are relevant to the changes to did.

Another important thing is to not only test the succesful cases but also the cases where things are expected to fail: Do the really fail, and do they fail in the way they are supposed to?

Writing tests can be quite boring, but having a good test suite that quickly tells you if everything is still in order is a really nice thing.

---

### Post by unittesting on 2011-07-12
> **pholding said:**
> Just wondering whether any other C++ developers on this forum have use a unit testing framework for their projects and if so how they deal with the issues I've encountered.
 
In the past I've just written a simple bit of code to call all of the functions passing in the relevent data and write the output to the console, however as the code base grows this doesn't seem a very scalable solution.

Have you tried a C++ mocking framework like Google Mocks or [Isolator++ for Linux]("http://www.typemock.com/isolatorpp-product-page?utm_source=ubuntuforum&utm_medium=structuring-unit-tests&utm_campaign=forum-post")?

---

