---
title: "How to run Perl script in Ubuntu 16.04Lts over terminal."
date: 2017-02-23
forum: New to Ubuntu
---

### Post by pipa2 on 2017-02-23
[FONT=arial]Hi There,



I have a question, I want to run a Perl script that I have and supposed to update password on the routers. My Linux knowledge isn't that great. I was wondering if someone could tell me how I can ran this script on the Ubuntu 16.04 terminal. 

 I've saved the main script on my desktop system as "[pass.pl]("http://pass.pl/")"and saved the password list that goes along with this scrips as "passwdlist.cfg".


Just wondering how I can run them both, so I can execute the script.


Thanks for your help.

[/FONT]
[FONT=arial]Pipa[/FONT]

---

### Post by TheFu on 2017-02-24
This is pretty basic knowledge - not perl specific. Just script specific.  Nobody can ensure the required dependencies are necessary for the script can work.  BTW - paying for something like this would never enter my mind.  Routers really shouldn't be using password-based authentication beyond the first 3 minutes of owning it. ssh-keys should be used instead.

Ok - so some basic knowledge ... you can get this from a good book - *The Linux Command Line* - it is a free, no hassle, PDF book. Or you can buy it at any bookstore. Any beginning Linux shell book would provide the same info.

```
# First, change the permissions bits to allow 'executing' the script; only needs to be done once.
$ chmod +x /path/to/file/pass.pl

# Next, just run the program
$ /path/to/file/pass.pl
```

You'll need to put the correct /path/to/file/ in for your system depending on where the script has been put. That is completely ON YOU do figure out.  It is a basic skill required on every Unix system.

---

### Post by pipa2 on 2017-02-25
Thanks for you help. Based on your details managed to run the script, but unfortunately I get an error message of "**Unrecognized character \xE2; marked by <-- HERE after swdfile = <-- HERE near column 18 at pass.pl line 15**" . 

When looking on the perl file itself as per the error lines mentioned above and from this phrase of  ** **my $passwdfile = &#8220;passwdlist.cfg&#8221;** **
columm 18 correspond to the (**&#8220;**) character quote on the beginning of **"**passwdlist.cfg". 

Could this be something wrong with the character used. Is there a substitute that could be used an instead?

Kind Regards,

Pipa

---

### Post by TheFu on 2017-02-25
If all you want to do is change passwords, take a look at 'expect' - it is a language just designed to automate interactive sessions.

However, passwords are so 1992.  Since ssh hit the world, using ssh-keys is THE way to go.  Hard to beat a 4K key using PKI compared any password. There isn't any comparison on the level of security offered. Passwords suck - even 50 character, random, passwords can't compare.

If you want to better understand this stuff - do some directed learning.  READ the first 131 pgs of this book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) Skim the rest of the book over 2-3 hrs to get a taste of possibilities. The early pgs provide background, set expectations, and help to get-your-mind-right for Linux.  Getting that background will make all the stuff around scripting better understood.  Scripting in bash, expect, perl, go, python, ... and 50 other languages - the basics are the same.

---

### Post by The Cog on 2017-02-26
> **pipa2 said:**
> Could this be something wrong with the character used. Is there a substitute that could be used an instead?


Yes indeed. You have been using a program that silently changes the text you paste into it. 
Have a close look at the double-quotes on ** my $passwdfile = &#8220;passwdlist.cfg&#8221; **. They are not normal quote characters and the perl interpreter will not recognise them. You should be using normal quote characters (") as would have been in the original script. Use an editor like gedit rather than an office suite that silently "corrects" your input.

EDIT:
For easy visual comparison:
```
my $passwdfile = &#8220;passwdlist.cfg&#8221; - bad
my $passwdfile = "passwdlist.cfg" - good
```

EDIT:
As TheFu points out below, the "helpful correction" to the quotes may have happened before even reaching the web server rather than during copy/paste from the web page by yourself. It's something to beware of whenever you copy scripts from web pages.

---

### Post by TheFu on 2017-02-26
Wow. I completely missed the issue!  Sorry.  Thanks to The Cog for seeing the real problem.

I'd add that copy/paste from online sources will usually alter the single and double quotes. My blog software does this, so it isn't safe to copy/paste commands from my blog. Even if they are inside _code_ tags, the quotes are often an issue.  IME, using an editor doesn't always fix the root problem, but definitely better and lighter than any word processing software (except Eclipse).  Geany, vim, emacs, Atom and 50 other options for _editors_ exist for Unix.  I've had to do global search-replaces inside my editor of choice for similar reasons.

---

