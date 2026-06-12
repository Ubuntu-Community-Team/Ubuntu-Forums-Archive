---
title: "scite+ruby help"
date: 2008-07-07
forum: Programming Talk
---

### Post by AnLGP on 2008-07-07
Hello,

I'm new to programming.  A friend recommended Ruby.  I downloaded that and scite.  I save the program with the .rb extension and hit "F5" to try and run it and it outputs this error:

>ruby p001hello.rb
sh: ruby: command not found
>Exit code: 127

Can anyone tell me what the issue is?  The only code I have in the program is

> puts 'Hello'

and I believe it's the correct code as I'm following a tutorial.  Thank you.

---

### Post by danbuter on 2008-07-07
I would use the terminal. After saving your file, go to terminal and type in ruby filename.rb and it should work.

---

### Post by AnLGP on 2008-07-07
Thank you it worked.  To get it to print the file I had to do the whole filename and that was

/home/steve/rubyprograms/p001hello.rb

Is there any way to shorten that for efficiency?  Thanks!

---

### Post by Ptero-4 on 2008-07-07
type
```
ruby ./filename.rb
```
from the directory where your ruby apps are (or alternatively add that directory to your PATH (this is done in the bash config files) and logout for making the changes permanent. After that 
```
ruby filename.rb
``` 
will be enough to run the app.

---

### Post by AnLGP on 2008-07-07
Add which directory?  The /rubyprograms?

---

### Post by nanotube on 2008-07-08
> **AnLGP said:**
> Add which directory?  The /rubyprograms?

/home/yourname/rubyprograms, yes.

i would suggest at this point that you should go through the cli tutorials at linuxcommand.org. it's a good idea to know how to operate the basics of shell, before you get into any "real" programming.

---

### Post by AnLGP on 2008-07-08
I've done those.  I can't say I have it memorized.

---

### Post by nanotube on 2008-07-08
> **AnLGP said:**
> I've done those.  I can't say I have it memorized.

ah, i see. :)

also, you could tweak scite's config files to be able to 'find' ruby. it really should be able to run your code with "f5", and that makes it mighty convenient. (i haven't run across this problem though - it finds python just fine for me).

if you can't find how to fix that, just keep a terminal window open, and cd'd to your rubyprograms directory. when you want to run it, just keep going arrow-up,enter to rerun your code. (arrow-up lets you go back in command history)

---

### Post by AnLGP on 2008-07-08
Thank you :)

---

### Post by chunky bacon! on 2011-01-24
I have a similar issue to the OP, and I was wondering if anyone could help.

I installed Ruby using[ this site's guide.]("http://ryanbigg.com/2010/12/ubuntu-ruby-rvm-rails-and-you/")  (Note: did not go through with Rails, yet).

From the command line, I can run my ruby files just fine.  However, from Scite, trying to execute the files using the F5 key yields "ruby not found."

ruby -v displays properly in the terminal 

"ruby 1.9.2p136 (2010-12-25 revision 30365) [i686-linux]"

Any idea where Scite is looking for Ruby?

---

### Post by kurum! on 2011-01-24
> **chunky bacon! said:**
> I have a similar issue to the OP, and I was wondering if anyone could help.

I installed Ruby using this site's guide.  (Note: did not go through with Rails, yet).

From the command line, I can run my ruby files just fine.  However, from Scite, trying to execute the files using the F5 key yields "ruby not found."

ruby -v displays properly in the terminal 

"ruby 1.9.2p136 (2010-12-25 revision 30365) [i686-linux]"

Any idea where Scite is looking for Ruby?

check Scites's options or preferences. There should be somewhere you can define all these paths to your Ruby environment

---

### Post by chunky bacon! on 2011-01-24
Whew.  OK, found it.  Putting it here in case it helps anyone else in the future.  

Doing a "which ruby" command in terminal gave me the path of:

/home/myusername/.rvm/rubies/ruby-1.9.2-p136/bin/ruby

Then, in Scite, it is Options>>Edit Properties>>Open ruby.properties

The lines are at the bottom of the file:

```
if PLAT_GTK
    command.go.*.rb= ruby $(FileNameExt)

    command.name.1.*.rb=Check Syntax
    command.1.*.rb= ruby (FileNameExt)

    command.name.2.*.rb=Code Profiler
    command.2.*.rb= ruby -r profile $(FileNameExt)
```Every line that has "ruby," I changed to the full path.

So it looks like this:

```
if PLAT_GTK
    command.go.*.rb=/home/myusername/.rvm/rubies/ruby-1.9.2-p136/bin/ruby $(FileNameExt)

    command.name.1.*.rb=Check Syntax
    command.1.*.rb=/home/myusername/.rvm/rubies/ruby-1.9.2-p136/bin/ruby -cw $(FileNameExt)

    command.name.2.*.rb=Code Profiler
    command.2.*.rb=/home/myusername/.rvm/rubies/ruby-1.9.2-p136/bin/ruby -r profile $(FileNameExt)


```As a sidenote, I could not by default save this, so I had to close Scite, open it from the terminal using gksu Scite, and then was able to save the configuration.

Voilà!  Hitting F5 now works!

---

