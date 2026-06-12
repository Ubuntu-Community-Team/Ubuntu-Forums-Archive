---
title: "Netbeans -&gt; Code::blocks"
date: 2008-09-02
forum: Programming Talk
---

### Post by StOoZ on 2008-09-02
I just moved from netbeans to code::blocks  , and its much faster than netbeans , and seems more mature , but , now I need to learn how to use it properly.. :(

anyhow , I feel that I did the right choice , im programming in C++ only.

---

### Post by StOoZ on 2008-09-02
oopps I forgot to ask the question : 
In netbeans , why I typed '#include<'  then all the system header  , libs popped up , in a list box , in netbeans , it doesnt happen , only my (custom headers) are shown, any idea how to fix it?

---

### Post by drubin on 2008-09-02
I do not know this IDE, But there are a whole bunch of editors in the stickies most of them link to tutorials with regards to using them.

---

### Post by StOoZ on 2008-09-08
anyone else is using this IDE?
Im having issues with the code completion , the plugin is enabled , but still , no code completion for stuff that is out of the program (not built by me).
for e.g : when I type : std::
nothing appers...
string str;
str.
nothing...
any idea how to solve it??
I dont think that C::B Codecompletion is that bad.

---

### Post by rnodal on 2008-09-08
Codeblocks is my favorite IDE. I use it to code my project in Linux and then to port it to Windows. About the headers question, I don't think they support that yet. 


-r

---

### Post by StOoZ on 2008-09-09
so what is the code completion plugin is for?

---

### Post by rnodal on 2008-09-09
I was referring to when you type #include and you only get you headers. C::B code competition works for me in the cases for example when you type std:: etc. What version are you using? I will look at my current settings later and see if there is anything that I think may make a difference. 

-r

---

### Post by StOoZ on 2008-09-09
im using the latest one from their site (not one of the nightly builds).
my settings are the default ones , with the code completion plugin enabled.
about the headers things (#include<...) , I can skip that , but I really need the code completion thing , when I type for e.g : std::  I want the list of function/methods etc.. it has..
at the moment , it shows it only for MY OWN classes.

---

### Post by rnodal on 2008-09-09
> **StOoZ said:**
> im using the latest one from their site (not one of the nightly builds).
my settings are the default ones , with the code completion plugin enabled.
about the headers things (#include<...) , I can skip that , but I really need the code completion thing , when I type for e.g : std::  I want the list of function/methods etc.. it has..
at the moment , it shows it only for MY OWN classes.

I was going to tell you that I really don't think the whole #include thing is that vital as code completion is but that is just my opinion. I use the nightly builds and also they repository for the deb files. I don't know if that has anything to do with it. If remember well even in version 8.02 it worked for me. Anyway, I will check my settings when I get home and report back to you. Take care until then.


-r

---

### Post by Mickeysofine1972 on 2008-09-09
Unfortunately C::B doesn't have this functionality yet

Although it worth mentioning that a basic knowledge of the more common headers will do you a big favor anyway as you might not always have the blessing of code complete.

I use C::B on all my c++ projects and would even entertain netbeans, (yes I gave it a go and it wasnt what I liked)

If you have any other questions about using C::B I will be happy to help though.

Mike

---

### Post by rnodal on 2008-09-09
> **Mickeysofine1972 said:**
> Unfortunately C::B doesn't have this functionality yet



Mike

What functionality are you talking about, displaying the headers when you type #include <(or ") or code completion at all? I DO get code completion when I type things like object. or object-> or std:: etc.

-r

---

### Post by rnodal on 2008-09-10
I checked C::B setting and these are the settings that I think can affect your code completion.

Settings->Editor->Code-completion and symbols browser
---->"Display info when hovering mouse..."
---->"Automatically launch when..."

Settings->Editor->C/C++ Parser
---->"Follow LOCAL"
---->"Follow GLOBAL"
---->"Parse preprocessor"

If this settings don't get it working for you then I have no idea. :(
C::B is not perfect but it gets the job done, at least for me. Take care,

-r

---

### Post by StOoZ on 2008-09-10
first of all , thanks , I set this feature '---->"Follow GLOBAL"' 
and now when I type for e.g 
std::

I get a list with only these options :
trl
_6
_debug
_norm


what the h*ck it wrong with this C::B?
im seriously thinking about returning to netbeans (I quite it since I couldnt configure Wxwidgets in windows on it)

---

### Post by rnodal on 2008-09-10
Have you include your headers? Also, do you mind trying the nightly builds? I have been using the nightly builds for over a year now and I must say that I have never had any problems.

-r

---

