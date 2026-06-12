---
title: "Configuraton file load order"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by starstreams on 2012-12-12
Hello, I'm trying to make sense of something with regard to *system wide* configuration files and *personal* config file locations and their loading order. Just to clarify: I understand that system wide config files load first and that they are in a different location then your personal config files which load next. The config files specific to your account override system wide settings. So I do understand that there is a certain order and priority. Here's my issue.

My book doesn't give a good example of how to verify which files load first. I'm running bin/bash shell.

**Question1:** I know it's not possible to verify the load order by reading config files in a text editor, but can I assume that when I view various config files from the terminal, the load order will be evident by where the output shows up in the displayed list? i..e  if one of the config files read-out shows at the bottom of the displayed list, would this indicate that the system read that config file first?

**Question2:** One location for system wide config files would be ([COLOR=Blue]/ect/profile[/COLOR]) for example: But are the personal config files specific to the account always located in the home directory? The reason I'm asking this is because my book is using an example by searching various personal config locations (separated paths), but the example shows the home shortcut **~/** in front of all the separated paths ..which indicates to me that they are searching the home directory. But I don't have any config files in my home directory. So I'm wondering at this point in time, if the "only" config files I have are system wide config files since I have not installed any applications for there to be any personal config files.


Thank you.

---

### Post by mikewhatever on 2012-12-13
There are lots of config files in home directories, usually hidden files beginning with a dot. Run **ls -a** in a terminal window to see them.

---

### Post by starstreams on 2012-12-13
Thank you mikewhatever, I didn't think of that, I can see all of them now. 
You're help is much appreciated!

I'm still not understanding something though. My book keeps telling me to write down the order in which the config files run. But the example they give in the picture below (attached) shows the home directory [COLOR=Blue]~/ [/COLOR]config files *and* the *system wide* [COLOR=Blue]/ect[/COLOR] config files loading out of order.. not consecutively: And they're using arrows to indicate the order I think.

I think this is the load order in the book's example:

**/etc**
[B]~/
~/
/etc[/B]

But in another sections of the book the author said that the *system wide *config's found in places like etc always load before the user configs. I got that part. But I don't understand why this list in the attached image is out of order then. Where does one confirm how the system loads the files? I have used the _set_ command to show the config settings. Are the locations displayed at the bottom of the set print out any indication that those files loaded first? Or last? How do I confirm the run order that the book keeps telling me to write down?
Or am I making too much out of this? 
In this case, can I just assume anything in ect usually runs first and anything in the home directory runs second, unless it's piggybacked?

[attach]228641[/attach]

Advanced Thanks

---

### Post by Cheesehead on 2012-12-13
See  [FONT="Courier New"]man bash[/FONT]

> When bash is invoked as an interactive login shell, or as a non-interactive shell with the --login option, it first reads and executes commands from the file /etc/profile, if that file exists.  After reading that file, it looks for ~/.bash_profile, ~/.bash_login, and ~/.profile, in  that order, and reads and executes commands from the first one that exists and is readable.  The --noprofile option may be used when  the shell is started to inhibit this behavior.

---

### Post by bab1 on 2012-12-14
> **starstreams said:**
> Thank you mikewhatever, I didn't think of that, I can see all of them now. 
You're help is much appreciated!

I'm still not understanding something though. My book keeps telling me to write down the order in which the config files run. But the example they give in the picture below (attached) shows the home directory [COLOR=Blue]~/ [/COLOR]config files *and* the *system wide* [COLOR=Blue]/ect[/COLOR] config files loading out of order.. not consecutively: And they're using arrows to indicate the order I think.
The book is only showing the bash (shell) config) files.  There are system config files and app config files too.

These days config order for system and application is in parallel and "on demand".  These are handled by upstart scripts on Ubuntu.  The old init scrpts were serialized (SysV init) > 

I think this is the load order in the book's example:

**/etc**
[B]~/
~/
/etc[/B]
The book is explaining how the login shell is configured, not the entire OS.  First the system wide shell profile is used.  Then, if interactive, the users personal BASH config files are used.  If the BASH shell is started by a process (app (a non-login shell), it is can use different config files.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://heimhardt.com/htdocs/bashrcs.html") for details.> 

But in another sections of the book the author said that the *system wide *config's found in places like etc always load before the user configs. I got that part. But I don't understand why this list in the attached image is out of order then. Where does one confirm how the system loads the files? I have used the _set_ command to show the config settings. Are the locations displayed at the bottom of the set print out any indication that those files loaded first? Or last? How do I confirm the run order that the book keeps telling me to write down?
Or am I making too much out of this? 
You are.  The system loads before you login and is not serialized anymore.> 
In this case, can I just assume anything in ect usually runs first and anything in the home directory runs second, unless it's piggybacked?

[attach]228641[/attach]

Advanced Thanks
Most things for the OS are configured via files in /etc/.  The users personal settings are in config files in that users home directory.

---

### Post by starstreams on 2012-12-14
**Thank you bab1**

> **bab1 said:**
> The book is only showing the bash (shell) config)  files.  There are system config files and app config files too. ...The  book is explaining how the login shell is configured, not the entire OS.   First the system wide shell profile is used.
Sorry about my confusion. It's just the book is calling the BASH shell,  what you're calling the *login shell* as the _session shell_.  But I guess we're talking about the same thing here. You'd think the  author of the book would be more clear on the fact that the example  demonstrated the bash shell exclusively since it's written with new  users in mind. I guess in this case, the loggin shell (which I think is called by the system via system wide files) loads first. And the BASH shell gets invoked by user configuration files? So the BASH shell  has more to do with user personal settings? I'm telling you, I've been  reading up on all this stuff like a mad man and watching different VTC videos, Lynda....ect. But the  structure and all the terminology makes it so confusing. It's like Wikipedia, you read one thing, only to find out that you have to keep digging into deeper unrelated topis just to understand what you read.



> **bab1 said:**
> 
These days config order for system and application is in parallel and  "on demand".  These are handled by upstart scripts on Ubuntu.  The old  init scrpts were serialized (SysV init)  I kind of understand  what you mean. I'll research serialized SysV init on my own to clarify  what you said here, but I think I have a basic idea what you're saying. 

> **bab1 said:**
> Then,  if interactive, the users personal BASH config files are used.  I've been seeing this interactive word a lot these days, I'm guessing  that just means anything other than the default OS that invokes the BASH  shell, or makes it do something outside of it's normal boot routine. Last night I was doing on search to find out what this [COLOR=Blue]--login option[/COLOR] was all about but couldn't find a definitive answer. I know it's related to a none interactive login.


> **Cheesehead said:**
> See  [FONT=Courier New]man bash[/FONT]
**Thanks cheesehead**, I wanted to comment on this last night before I read bab1's response today.
I have to be honest, 90% of these man pages are still beyond my understanding at this point, but I'm slowly picking things up. As someone else mentioned on the boards, Man pages are more reference for people who already understand the syntax and other concepts. Some of the examples in them make no sense to me at all. Like for example under INVOCATION it reads:
[COLOR=Blue]A _login shell_ is one whose first character of arguments zero is a -, or one started with the  --login option[/COLOR].

The above line sounds like something you would say to someone who understand scripting.
It's unrelated to what we're talking about, but I just wanted to make the point that this type of language structure to a new Linux user leaves them scratching their head. So I'm basically out trying to translate these types of examples. That's pretty much why I'm posting in Absolute Beginners Section. If I understood how to read the man pages, I would just do that. However, after reading bab1's post,  the quoted text you posted cheese made much more sense to me. So I do very much appreciate you posting that text. I probably would have never thought of checking the man page on bash had you not have said something. I guess I'm just gowning from the pain of learning. :p
I've written some XHTML and CSS so I can appreciate how the language differences sound to someone who has never looked at it. But the experience for me was, learning XHTML from books was always straight forward explanations. however, these Man pages are horrible if you don't already know something. 

The text you quoted from the man page only listed one system wide config file located in the ect directory. So back to the original question. I was wondering how a complete beginner is able to track down all the files being loaded. Both by the *login-shell-system-wide* configs as well as any *user session-BASH* configs and their load order. I'm just trying to find a solid system I can use to investigate how the system loads all these files. Sorry if I'm repeating what was already explained, I'm still trying to make sense of all this.
**Back @ bab1**
I do understand the basic idea of what you said I think: That is.. that there is a login shell sourced/ loaded by the system, and then anything else called by the user config files calls to the BASH. I just don't know how to track all of them in case I wanted to make a list to have a  record to refer back on. Like how do you track every config file loaded in the system.

---

### Post by bab1 on 2012-12-14
> **starstreams said:**
> **Thank you bab1**


Sorry about my confusion. It's just the book is calling the BASH shell, or what you're calling the *login shell* as a the _session shell_.  But I guess we're talking about the same thing here. You'd think the  author of the book would be more clear on the fact that the example  demonstrated the bash shell exclusively since it's written with new  users in mind. I guess in this case, the loggin shell (which I think is called by the system via system wide files) loads first. And the BASH shell gets invoked by user configuration files? So the BASH shell  has more to do with user personal settings? I'm telling you, I've been  reading up on all this stuff like a mad man and watching different VTC videos, Lynda....ect. But the  structure and all the terminology makes it so confusing. It's like Wikipedia, you read one thing, only to find out that you have to keep digging into deeper unrelated topis just to understand what you read.



 I kind of understand  what you mean. I'll reseach serialized SysV init on my own to clarify  what you said here, but I think I have a basic idea what you're saying. 

  I've been seeing this interactive word a lot these days, I'm guessing  that just means anything other than the default OS that invokes the BASH  shell, or makes it do something outside of it's normal boot routine. Last night I was doing on search to find out what this [COLOR=Blue]--login option[/COLOR] was all about but couldn't find a definitive answer. I know it's related to a none interactive login.



**Thanks cheesehead**, I wanted to comment on this last night before I read bab1's response today.
I have to be honest, 90% of these man pages are still beyond my understanding at this point, but I'm slowly picking things up. As someone else mentioned on the boards, Man pages are more reference for people who alreayd understand the syntax and other concepts. Some of the examples in them make no sense to me at all. Like for example under INVOCATION it reads:
[COLOR=Blue]A _login shell_ is one whose first character of arguments zero is a -, or one started with the  --login option[/COLOR].

The above line sounds like something you would say to someone who understand scripting.
It's unrelated to what we're talking about, but I just wanted to make the point that this type of language structure to a new Linux user leaves them scratching their head. So I'm basically out trying to translate these types of examples. That's pretty much why I'm posting in Absolute Beginners Section. If I understood how to read the man pages, I would just do that. However, after reading bab1's post, your the quoted text you posted cheese made much more sense to me. It's much appreciated. I guess I'm just growning about the pain of learning. :p
I've written some XHTML and CCS so I can appreciate the difference is language differences from common conversation. But the difference is, learning XHTML from books were always straight forward explanations. These Man pages, are horrible if you don't already know something.

The text you quoted from the man page only listed one system wide config file located in the ect directory. So back to the original question. I was wondering how a complete beginner is able to track down all the files being loaded. Both by the *login-shell-system-wide* configs as well as any *user session-BASH* configs and their load order. I'm just trying to find a solid system I can use to investigate how the system loads all these files. Sorry if I'm repeating what was already explained, I'm still trying to make sense of all this.
**Back @ bab1**
I do understand what you said in that, there are login shells sourced, or loaded, and then anything else called by the user config files to call on the BASH. I just don't know how to track all this down if I wanted to make a list for my record.

:-)

If you want the *load order *of all the processes and the user that spawned them you might look at the output from this command (used at the terminal command line (CLI))```
ps -ef
```

This is a listing of all the processes running on your machine.  The are listed in the order they were started (see the Process ID (PID)).  To create a file in you home directory named process.txt use this command ```
ps -ef > process.txt
```

---

### Post by starstreams on 2012-12-14
> **bab1 said:**
> The system loads before you login and is not serialized anymore.

What exactly does that mean? If something is loading in serial it would seem to load one after the other. First the *system configs* and then* user configs*. 
But you're saying it's not serial anymore.
I just searched a ton of linux combination worlds with the term serialized and got all kind of unrelated scripting examples.
I did read up on the older V system init.d and init, so it makes sense that the newer upstart scripts are now used. But to fully understand it, I probably need to get my head into scripting or I'm always going to be lost talking to people.
With regard to the PS command,  it looks like these are not only running processes/services, but configs that were loaded at some point? Interesting. I have read about the *ps* command, but I just thought it was for currently running daemons only.

---

