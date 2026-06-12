---
title: "Beginner Programming Challeng #2"
date: 2011-07-16
forum: Programming Talk
---

### Post by Randy Flagg on 2011-07-16
Okay, here is the original post:

[http://ubuntuforums.org/showthread.php?p=5531236#post5531236](http://ubuntuforums.org/showthread.php?p=5531236#post5531236)

It took me two days to write this and a day to go through the entries and fix what I had so badly screwed up.  I think the end result is pretty good but I am sure there is still room for lot's of improvement.  But if you think this bad.  You should have seen the original.  I will post it if anyone wants a good chuckle.

Again, please let me know your comments.  They really helped me last time.

Thanks and here it is:


[PHP]
#!/usr/bin/env python
#
#Ubuntu Forums Beginner Challenge 2
#Take user input for fourm name, age, forum id and then print
#out a sentence using those variables

import string
import sys

class foruminfo:
    
    #Definds global list and displays open message
    def __init__(self):
        self.end_out = []
        print '\nThis is a program to prompt for your forum name, forum id, and age.'
        print 'Type Quit at any time to exit the program\n'


    #Checks at any prompt if the user time quit or exit
    def exit_prog_chk(self, response):
        if response.lower() == 'quit': sys.exit(0)        
        if response.lower() == 'exit': sys.exit(0)
        
    #Checks to see if the name enter is valid.
    #The name must be less than 21 character, valid numbers or letter, and
    #should not be a CR or start with a space.#returns 1 if valid and 0 if not
    def name_valid(self, name):
        check = 1
        if 0 < len(name) < 21:
            i = 0
            if not name.startswith(' '):
                valid_chars = string.ascii_letters + string.digits +                               string.punctuation + ' '    
                while i < len(name):
                    if name[i] not in valid_chars:
                        check = 0
                    i += 1
            else: check = 0
        else: check = 0
        return check
    
    #Checks to see if age is a number between 1-99    
    def age_valid(self, ageinp):
        check = 1
        i = 0
        if len(ageinp) > 0:
            while i < len(ageinp):
                if ageinp[i] not in string.digits:
                    check = 0
                else:
                    if int(ageinp) not in range(1,99):
                        check = 0
                i += 1
        else: check = 0
        return check
        
    #Checks to see if ID is a number between 1 and 999999
    def id_valid(self,idinp):
        check = 1
        i = 0
        if 0 < len(idinp) < 7:
            while i < len(idinp):
                if idinp[i] not in string.digits:
                    check = 0
                i += 1
            if idinp == '0':
                check = 0
        else: check = 0
        return check


    #Gets the name input, checks for quit or validity.
    #If valid it adds it to the global list
    def get_name(self):
    
        name_fail = '\n***Name must contain valid letters, numbers\nor punctuation and be less than 20 characters***\n'

        print 'Please enter a Forum Name or quit to exit.'
        forumname = raw_input('Forum Name: ')
        self.exit_prog_chk(forumname)
        if self.name_valid(forumname):
            self.end_out.append(forumname)
        else:
            print name_fail
            self.get_name()

    #Gets user input age, checks for quit and validity
    #If valid add it and age + 1 to global list
    def get_age(self):
        age_fail = '\nPlease enter correct age or quit to exit.'

        print '\n',
        age = raw_input('Age: ')
        self.exit_prog_chk(age)
        if self.age_valid(age):
            self.end_out.append(age)
            self.end_out.append(int(age) + 1)
        else:
            print age_fail
            self.get_age()

    #Gets user ID input, checks for quit and validity
    #If valid add it and ID + 1 to global list
    def get_id(self):

        id_fail = '\nPlease print a valid ID between 1 and 999999 or quit to exit.'

        print '\n',
        forumID = raw_input('Forum ID: ')
        self.exit_prog_chk(forumID)
        if self.id_valid(forumID):
            self.end_out.append(forumID)
            self.end_out.append(int(forumID) + 1)
        else:
            print id_fail
            self.get_id()


    #Display global list
    def display(self):
        print '\nYou are {0}, aged {1}, next year you will be {2}'.format(
                            self.end_out[0], self.end_out[1], self.end_out[2]),
        print ', with user ID {0},\nthe next user is {1}'.format(
                                            self.end_out[3], self.end_out[4])

if __name__ == "__main__":
    forum = foruminfo()
    forum.get_name()
    forum.get_age()
    forum.get_id()
    forum.display()
[/PHP]

---

### Post by Bachstelze on 2011-07-16
[php]    def get_name(self):
    
        name_fail = '\n***Name must contain valid letters, numbers\nor punctuation and be less than 20 characters***\n'

        print 'Please enter a Forum Name or quit to exit.'
        forumname = raw_input('Forum Name: ')
        self.exit_prog_chk(forumname)
        if self.name_valid(forumname):
            self.end_out.append(forumname)
        else:
            print name_fail
            self.get_name()[/php]

Not good. If a malicious user repeatedly enters an invalid name, you will get a stack overflow (or its Python equivalent) from all the calls to get_name(), and your program will crash. Better:

[php]    def get_name(self):
    
        name_fail = '\n***Name must contain valid letters, numbers\nor punctuation and be less than 20 characters***\n'

        while True:
            print 'Please enter a Forum Name or quit to exit.'
            forumname = raw_input('Forum Name: ')
            self.exit_prog_chk(forumname)
            if self.name_valid(forumname):
                self.end_out.append(forumname)
                break
            else:
                print name_fail[/php]

Also:

[php]            else: check = 0[/php]

Bad Python practice, make it

[php]            else:
                     check = 0[/php]

And why use 1/0 for the value of check? Python has booleans True/False.

[php]        if response.lower() == 'quit': sys.exit(0)        
        if response.lower() == 'exit': sys.exit(0)[/php]

Make it

[php]        if response.lower() == 'quit' or response.lower() == 'exit':
                  sys.exit(0)[/php]

[php]    def id_valid(self,idinp):
        check = 1
        i = 0
        if 0 < len(idinp) < 7:
            while i < len(idinp):
                if idinp[i] not in string.digits:
                    check = 0
                i += 1
            if idinp == '0':
                check = 0
        else: check = 0
        return check
[/php]

There are better ways to check whether a string is an int:

[php]    def id_valid(self,idinp):
        try:
            n = int(idinp)
            if 0 < n < 1000000:
                check = 1
            else:
                check = 0
        except ValueError:
            check = 0
        return check
[/php]

---

### Post by TwoEars on 2011-07-16
```
class foruminfo:
```

Nope, that's not how we name classes in Python. It should be ForumInfo. Read [http://www.python.org/dev/peps/pep-0008/](http://www.python.org/dev/peps/pep-0008/)

```

class foruminfo:
    
    #Definds global list and displays open message
```
Are you sure that's what the foruminfo class does?  Your documentation should be IN the method or class that it's talking about, for example - 

```

class foruminfo:
    
    
    def __init__(self):
        #Defines global list and displays open message
        self.end_out = []
        print '\nThis is a program to prompt for your forum name, forum id, and age.'
        print 'Type Quit at any time to exit the program\n'
```

self.end_out is an internal attribute, and as such should be prefixed with "__".
I also suggest using """ DOCUMENTATION """ instead, where documentation is your documentation ;)

```
def exit_prog_chk(self, response):
```
This isn't a great name. To me, this will check if the program is being exited, not that it exits the program.

Also, all internal methods should have the prefix "_". 

```
 if response.lower() == 'quit': sys.exit(0)        
        if response.lower() == 'exit': sys.exit(0)
```

As Bachstelze said, you can simplify this into 

```

if response.lower() == 'quit' or response.lower() == 'exit':
            sys.exit(0)
```


```
def name_valid(self, name):
        check = 1
        if 0 < len(name) < 21:
            i = 0
            if not name.startswith(' '):
                valid_chars = string.ascii_letters + string.digits +                               string.punctuation + ' '    
                while i < len(name):
                    if name[i] not in valid_chars:
                        check = 0
                    i += 1
            else: check = 0
        else: check = 0
        return check
```
You could use the re module here, for example - 

```
def _name_valid(self, name):
        if re.match('\w{1,20}[^a-z]',name) is None:
            return False
        return True
```
Of course, this example isn't feature complete, that's for you to do ;)


```

def age_valid(self, ageinp):
        check = 1
        i = 0
        if len(ageinp) > 0:
            while i < len(ageinp):
                if ageinp[i] not in string.digits:
                    check = 0
                else:
                    if int(ageinp) not in range(1,99):
                        check = 0
                i += 1
        else: check = 0
        return check
```
This isn't a nice method. ageinp is a bad name too, not sure what it's meant to be instead of "age".

How about this instead -

```

def _age_valid(self, age):
        if age.isdigit() and 1<=int(age)<100:
            return True
        return False

```


```
def id_valid(self,idinp):
        check = 1
        i = 0
        if 0 < len(idinp) < 7:
            while i < len(idinp):
                if idinp[i] not in string.digits:
                    check = 0
                i += 1
            if idinp == '0':
                check = 0
        else: check = 0
        return check
```

Again, another nasty method. Same comment about idinp as ageinp

How about

```

def _id_valid(self, ID):
        if ID.isdigit() and 1<=int(ID)<999999:
            return True
        return False

```

Bonus points if you can create a method that stops you having two almost identical methods ;)

```

print '\nYou are {0}, aged {1}, next year you will be {2}'.format(
                            self.end_out[0], self.end_out[1], self.end_out[2]),
```

I'd say that's bad usage of a list (end_out). You should use a dict instead - what if someone calls the methods in the wrong order?

---

### Post by CuracaoThe on 2011-07-16
[My solution written in Ruby]("https://github.com/curacao/ubuntutasks/blob/master/lib/ubuntutasks/02_forummember.rb"). Sorry for cluttering your thread, but maybe someone would be interested in this.

[PHP]
class ForumMember
  attr_accessor :input, :output
  attr_reader :name, :age, :user_id

  def initialize
    @input = $stdin
    @output = $stdout
    fill_with_data
  end

  def fill_with_data
    puts "To exit this program, type an 'exit' keyword."
    @name = ask_for(:name)
    @age = ask_for(:age)
    @user_id = ask_for(:user_id)
    [@name, @age, @user_id]
  end

  # ForumMember object representation.
  #
  def to_s
    "You are #{name}, aged #{age} next year you will be #{age.to_i + 1}," +
    " with user id #{user_id}, the next user is #{user_id.to_i + 1}"
  end

  # There are two handy methods for tests: puts and gets.
  # https://gist.github.com/1061527
  #
  def puts(*args)
    @output.puts(*args)
  end

  def gets(*args)
    @input.gets(*args)
  end

  private

  # Ask user for some data to create new forum member.
  #
  def ask_for(data)
    loop do
      puts "Enter the #{data.to_s}: "
      input = gets.chomp
      exit if input == "exit" # 'exit' keyword handling.
      if valid?(data => input)
        input = shorten(input)
        return input
      end
    end
  end

  # Check whether user's input is valid.
  #
  def valid?(input)
    valid_range = 1..999999
    if input[:name] =~ /^[^\s][\w\s]+$/i or
       valid_range.member?(input[:age].to_i) or
       valid_range.member?(input[:user_id].to_i)

      return true
    else
      puts "Incorrect input!"
      return false
    end
  end

  # Truncate long values, e.g. name.
  #
  def shorten(phrase, length=19)
    if phrase.size > length
      phrase[0..length] + "..."
    else
      phrase
    end
  end

end

member = ForumMember.new
[/PHP]

---

### Post by Randy Flagg on 2011-07-17
Thanks, I appreciate the help again.  I implemented what I understood from both of your comments and change a couple of other things for the better.  I have a couple of questions below and will post the new code at the end.






> **TwoEars said:**
> 
```
def exit_prog_chk(self, response):
```This isn't a great name. To me, this will check if the program is being exited, not that it exits the program.

Also, all internal methods should have the prefix "_". 



I am a little confused here with both statemets.  This does actually exit the program.

I must confess I am still a little confused by the OOP aspects and the naming conventions (even though I have tried to read up on it more).

So should every method name start with with __ and also every internal object??

 
> **TwoEars said:**
> 
```
def _name_valid(self, name):
        if re.match('\w{1,20}[^a-z]',name) is None:
            return False
        return True
```Of course, this example isn't feature complete, that's for you to do ;)


I read up on this a little bit but I don't understand the "{1,20}[^a-z]"

couldn't I just use:

```

if re.match('\w', name) is None:

```[PHP]
#!/usr/bin/env python
#
#Ubuntu Forums Beginner Challenge 2
#Take user input for fourm name, age, forum id and then print
#out a sentence using those variables

import string
import sys

class ForumInfo:
    
    def __init__(self):
    #Definds global list and displays open message
        self.end_out = {}
        print '\nThis is a program to prompt for your forum name, forum id, and age.'
        print 'Type Quit at any time to exit the program\n'


    def exit_prog_chk(self, response):
    #Checks at any prompt if the user time quit or exit    
        if response.lower() == 'quit' or response.lower() == 'exit': 
            sys.exit(0)
        
    def name_valid(self, name):
    #Checks to see if the name enter is valid.
    #The name must be less than 21 character, valid numbers or letter, and      #should not be a CR or start with a space.     
        if 0 < len(name) < 21:
            if not name.startswith(' '):
                valid_chars = string.ascii_letters + string.digits +                               string.punctuation + ' '
                for i in name:
                    if i not in valid_chars:
                        return False
                    else: return True
            else: 
                return False
        else: 
            return False
        
    
    def age_valid(self, age):
    #Checks to see if age is a number between 1-99
        try:
            n = int(age)            
            if 0 < n < 100:
                return True
            else:
                return False
        except ValueError:
            return False
            
    def id_valid(self,ID):
    #Checks to see if ID is a number between 1 and 999999    
        try: 
            n = int(ID)
            if 0 < n < 1000000:
                return True
            else:
                False
        except ValueError:
            return False
        
    
    def get_name(self):
    #Gets the name input, checks for quit or validity.
    #If valid it adds it to the global list
    
        name_fail = '\n***Name must contain valid letters, numbers\nor punctuation and be less than 20 characters***\n'

        while True:
            print 'Please enter a Forum Name or quit to exit.\n'
            forumname = raw_input('Forum Name: ')
            self.exit_prog_chk(forumname)
            if self.name_valid(forumname):
                self.end_out['name'] = forumname
                break
            else:
                print name_fail
    
    def get_age(self):
    #Gets user input age, checks for quit and validity
    #If valid add it and age + 1 to global list
        while True:
            age_fail = '\nPlease enter correct age or quit to exit.'
            age = raw_input('\nAge: ')
            self.exit_prog_chk(age)
            if self.age_valid(age):
                self.end_out['age'] = age
                self.end_out['agep1'] = int(age) + 1
                break
            else:
                print age_fail
            

    def get_id(self):
    #Gets user ID input, checks for quit and validity
    #If valid add it and ID + 1 to global list

        id_fail = '\nPlease print a valid ID between 1 and 999999 or quit to exit.'
        while True:
            forumID = raw_input('\nForum ID: ')
            self.exit_prog_chk(forumID)
            if self.id_valid(forumID):
                self.end_out['ID'] = forumID
                self.end_out['IDp1'] = int(forumID) + 1
                break
            else:
                print id_fail
            


    def display(self):
    #Display global list    
        print '\nYou are {0}, aged {1}, next year you will be {2}'.format(
                            self.end_out['name'], self.end_out['age'],                                 self.end_out['agep1']),
        print ', with user ID {0},\nthe next user is {1}\n'.format(
                                            self.end_out['ID'],                                             self.end_out['IDp1'])
        
if __name__ == "__main__":
    forum = ForumInfo()
    forum.get_name()
    forum.get_age()
    forum.get_id()
    forum.display()
[/PHP]

---

### Post by TwoEars on 2011-07-17
> **Randy Flagg said:**
> 



I am a little confused here with both statemets.  This does actually exit the program.

I must confess I am still a little confused by the OOP aspects and the naming conventions (even though I have tried to read up on it more).

So should every method name start with with __ and also every internal object??

My comment was not on what the method does, but on what the method name suggests it does ;)

Every _internal_ (private) object/method/etc name should start with "_" - it prevents them being imported when calling ```
from Class import *
```
it also makes for more readable code.

Every class attribute name should start with "__".



 

> 
I read up on this a little bit but I don't understand the "{1,20}[^a-z]"

couldn't I just use:

```

if re.match('\w', name) is None:

```


Yes, you could, but it doesn't define the length of the name, so it could be a valid name in everyway except length.



Note for documentation - 
it should look like -
```

def method():
    """Hello, this is my documenation
    Writing it like this is easier to read"""
    return True

```

---

### Post by Randy Flagg on 2011-07-17
I think I get it. So you are saying it should be just exit_program.

Could you provide a sample from my code as to what should be _ and __?

So if I use the {1,20} it will return a null if the string is 21 characters long?

What about the [^a,z] wouldnt that exclude a-z?

I get what u r saying about the docs now.  Put them like that and they will show up in __doc__.

---

### Post by TwoEars on 2011-07-17
> **Randy Flagg said:**
> I think I get it. So you are saying it should be just exit_program.

Could you provide a sample from my code as to what should be _ and __?

So if I use the {1,20} it will return a null if the string is 21 characters long?

What about the [^a,z] wouldnt that exclude a-z?

I get what u r saying about the docs now.  Put them like that and they will show up in __doc__.

1) Exactly! :D

2) age_valid should be _age_valid as it should only be called by the class itself. self.end_out = {} should be self.__end_out, as it is a class attribute.

3) \w{1,20} will match anything with at least 1 to 20 word characters at the start if using re.match. \w{1,20}[^a-z] will match 1 to 20 word characters ONLY - they must not be followed by the characters from a-z. Hope this helps.

4) Exactly :D

---

### Post by Randy Flagg on 2011-07-17
This re thing is driving me crazy and I am finding the documentation on it poor at best so I am going to break it down into pieced to see if I have it right.

re.match() object basically matches a pattern to a string.  If the pattern matches you get a value returned that is something like a memory location(not important for my uses).  If it doesn't match it returns a null which is what I am looking for.

Also, the important difference between re.match and re.search is that re.match always start searching at the beginning of the string.

re.match(x, y) The first argument is the pattern.  The second one is the string to match the pattern to.  So:

re.match('a', 'abcd') would give me a match but:

re.match('e', 'abcd') would not.

re.match('\w', y) '\w' represent the range [A-Z,a-z,0-9,'_'].  So basically if my entire string contains only character in that rage it will return a value.

So this returns a value:

re.match('\w', 'abcd')

Okay, so we go back to your original suggestion:

re.match('\w{1,20}[^a-z]', name) 

This means look for a pair of characters [\w(anything one in that set) and ^a-z(anything not in a-z)] a minimum of 1 time and a max of twenty times.

this returns a true value if it finds anything like:

'a#dddd'
'vddsf&'

and a false value for something like 

'adsfsd'
'vdvdd'

That doesn't work for a couple of reasons.  First if I have:

'%adssadf'

That will return a false value because it didn't find a good letter followed by a bad.

Second, it doesn't take into account the string length at all.  The 20 just means it will look for 20 instances.  If it finds any number of instances between 1 and 20 it will return a true value.  It doesn't matter how long the string is.

So, please tell me I am missing something because I have been looking at this for hours and can't find a way to make it work.

---

### Post by TwoEars on 2011-07-18
> **Randy Flagg said:**
> This re thing is driving me crazy and I am finding the documentation on it poor at best so I am going to break it down into pieced to see if I have it right.

re.match() object basically matches a pattern to a string.  If the pattern matches you get a value returned that is something like a memory location(not important for my uses).  If it doesn't match it returns a null which is what I am looking for.

Also, the important difference between re.match and re.search is that re.match always start searching at the beginning of the string.

re.match(x, y) The first argument is the pattern.  The second one is the string to match the pattern to.  So:

re.match('a', 'abcd') would give me a match but:

re.match('e', 'abcd') would not.

re.match('\w', y) '\w' represent the range [A-Z,a-z,0-9,'_'].  So basically if my entire string contains only character in that rage it will return a value.

So this returns a value:

re.match('\w', 'abcd')

Okay, so we go back to your original suggestion:

re.match('\w{1,20}[^a-z]', name) 

This means look for a pair of characters [\w(anything one in that set) and ^a-z(anything not in a-z)] a minimum of 1 time and a max of twenty times.

this returns a true value if it finds anything like:

'a#dddd'
'vddsf&'

and a false value for something like 

'adsfsd'
'vdvdd'

That doesn't work for a couple of reasons.  First if I have:

'%adssadf'

That will return a false value because it didn't find a good letter followed by a bad.

Second, it doesn't take into account the string length at all.  The 20 just means it will look for 20 instances.  If it finds any number of instances between 1 and 20 it will return a true value.  It doesn't matter how long the string is.

So, please tell me I am missing something because I have been looking at this for hours and can't find a way to make it work.

Well, that was meant to just point you in the right place, not to do it for you ;)

The \w{1,20} will mean it matches between 1 and 20 inclusive word characters.

The [^a-z] will mean it must not be a character in the set a-z

Both of them together means it matches between 1 and 20 inclusive word characters not followed by a-z. This limits it (sort of) to 20 word characters alone.

Anyway, if you want a realistic example, how about -

```

re.match("\w{1,20}$", text)

```

That'll match 1-20 word characters that must be at the end of the string, and since match starts at the start of the string, it must match the whole string.

---

### Post by Randy Flagg on 2011-07-18
Okay, I just read through the dive into section on re.search.  I probably should have just read that from the start.  It seems that re.match isn't actually used that much and some people even suggest replacing it with re.search(^.....)

So:


re.match("\w{1,20}$", text)
This does work and I get what it is doing but the only non alphanumber char it will recognize is '_'.  I didn't see any reference to a '\' that would do punctuation so then I would have to put it in manually which would probably make it as bad as the original.

Again, thanks for the help.  I am chalking this one up to done and moving on to Challenge #3.

---

### Post by TwoEars on 2011-07-18
> **Randy Flagg said:**
> Okay, I just read through the dive into section on re.search.  I probably should have just read that from the start.  It seems that re.match isn't actually used that much and some people even suggest replacing it with re.search(^.....)

So:


re.match("\w{1,20}$", text)
This does work and I get what it is doing but the only non alphanumber char it will recognize is '_'.  I didn't see any reference to a '\' that would do punctuation so then I would have to put it in manually which would probably make it as bad as the original.

Again, thanks for the help.  I am chalking this one up to done and moving on to Challenge #3.

re.match is used quite a lot in production code. Not quite sure where you got that information from, because it's not well researched. I think I use match much more than search - people that are using search are usually doing it wrong. Anyway, I gave you a pointer to something that might help simplify your code, if you don't want to use it, that's fine, I won't take offence :)

---

### Post by Randy Flagg on 2011-07-18
> **TwoEars said:**
> re.match is used quite a lot in production code. Not quite sure where you got that information from, because it's not well researched. I think I use match much more than search - people that are using search are usually doing it wrong. Anyway, I gave you a pointer to something that might help simplify your code, if you don't want to use it, that's fine, I won't take offence :)

No worries, i learned alot about re which is going to help down the line.  That is why I am on these forums.  You can only learn so much from a book.

---

