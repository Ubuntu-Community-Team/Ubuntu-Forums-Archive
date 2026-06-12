---
title: "What does # before a linux command mean?"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by newhere_m on 2012-09-19
I read somewhere one should use command "# find ...." for some purpose. Can anybody please explain what the '#' mark before a command mean in linux?

---

### Post by hypnot0ad on 2012-09-19
Where did you read this?

---

### Post by Pand5461 on 2012-09-19
Unix shells usually show $ in the end of command prompt for an ordinary user, and # for the root user (try "sudo su" and see for yourself). So, "# find " is "find" run by root.

---

### Post by MG&amp;TL on 2012-09-19
> **newhere_m said:**
> I read somewhere one should use command "# find ...." for some purpose. Can anybody please explain what the '#' mark before a command mean in linux?

```
#blahblah
```

Is a comment in most shells. E.g. it won't do anything, just sit there looking pretty.

UNLESS it's something that requires root permissions, in which case they're indicating you should the perform the command as root. In Ubuntu, just prepend 'sudo' to it:

```
sudo find ...
```

Context would be helpful. :)

---

### Post by hypnot0ad on 2012-09-19
> **MG&TL said:**
> ```
#blahblah
```

Is a comment in most shells. E.g. it won't do anything, just sit there looking pretty.

UNLESS it's something that requires root permissions, in which case they're indicating you should the perform the command as root. In Ubuntu, just prepend 'sudo' to it:

```
sudo find ...
```

Context would be helpful. :)
Five:KSpost

---

### Post by newhere_m on 2012-09-20
Ok, I am giving below the context where the suggestion was made: The command to look for configuration files was given to be:

# find / -iname *.confSo this means really: sudo find / -iname *.conf
Thanks for all the replies.

---

### Post by jrog on 2012-09-20
> **newhere_m said:**
> Ok, I am giving below the context where the suggestion was made: The command to look for configuration files was given to be:

# find / -iname *.confSo this means really: sudo find / -iname *.conf
Thanks for all the replies.
In that context, the '#' indicates that this command should be run as the root user; so, yes, you're right that you should use sudo.

---

### Post by qamelian on 2012-09-20
> **newhere_m said:**
> Ok, I am giving below the context where the suggestion was made: The command to look for configuration files was given to be:

# find / -iname *.confSo this means really: sudo find / -iname *.conf
Thanks for all the replies.
That line as written is only a comment. Any line of code beginning with # is only a comment and will not be executed, as already explained above by [MG&TL]("http://ubuntuforums.org/member.php?u=1320682").

It would be helpful if you posted the entire context from which this comment has been extracted. Without seeing it in its full context, it is difficult for anyone to give you a genuinely helpful and accurate answer. :)

---

### Post by qamelian on 2012-09-20
> **jrog said:**
> In that context, the '#' indicates that this command should be run as the root user; so, yes, you're right that you should use sudo.
That is note what # at the beginning of a line means. I think you're getting it confused with the # that appears at the end of a shell prompt when you are logged in as root.

---

### Post by jrog on 2012-09-20
> **qamelian said:**
> That is note what # at the beginning of a line means. I think you're getting it confused with the # that appears at the end of a shell prompt when you are logged in as root.
The OP said that this was "a command to be given to search for configuration files." The command was given as:

# find / -iname *.conf

It looks to me that that is indicating that he should run the command as root. The context obviously suggests this, because if you run that command as a non-root user, you will get a number of messages saying that permission has been denied (since you can't read through all the folders under /). 

So yes, it's true that '#' at the beginning of the line in a script is the symbol for a comment. But in this context, this is a command that the OP is supposed to enter; he's not reading a script file, as far as I can tell. So, I actually think that, in this context, the '#' means what I said it means.

EDIT: I'm assuming that the little bit in the OP's post that says this (the bolded portion, anyway) is something that the OP added as his own guess for what the command means. I'm assuming that it wasn't something that was written in what the OP was reading:

> **newhere_m said:**
> 
# find / -iname *.conf**So this means really: sudo find / -iname *.conf**


Is this right, OP? The document you are reading says to run the following command to search for configuration files, and then it says this:

# find / -iname *.conf

If so, then, as I said, the '#' indicates a root prompt, not a comment.

---

### Post by qamelian on 2012-09-20
> **jrog said:**
> The OP said that this was "a command to be given to search for configuration files." The command was given as:

# find / -iname *.conf

It looks to me that that is indicating that he should run the command as root. 
As I said to the OP, the full context is needed. Preceding a command with a # never indicates that it should be run as root. It does always indicate a comment.

---

### Post by jrog on 2012-09-20
> **qamelian said:**
> As I said to the OP, the full context is needed. Preceding a command with a # never indicates that it should be run as root. It does always indicate a comment.
I'm sorry, but it seems to me that you may be being willfully pedantic about this (if not, I apologize). Look at this tutorial, as just one example of what I'm talking about: [https://wiki.archlinux.org/index.php/Change_username](https://wiki.archlinux.org/index.php/Change_username)

The '#' there means that the command should be run as root. Have you honestly never seen this before? Writing a command in this way in a tutorial, so as to indicate that the command should be run as a user with administrative privileges, is a pretty standard convention, and it seems to be exactly what is going on in the context of what the OP is referring to.

That said, yes, if a command is actually typed out by the user with a '#' before it (e.g., in a shell script, or at the command line), then it is a comment (assuming we're discussing Unix-style shells). But in terms of helping the OP actually understand what he is currently looking at, the present case looks like a case where he is being instructed to run a command as the root user.

---

### Post by malspa on 2012-09-20
> **jrog said:**
> But in terms of helping the OP actually understand what he is currently looking at, the present case looks like a case where he is being instructed to run a command as the root user.

That's how I see it, too.

---

### Post by qamelian on 2012-09-20
> **jrog said:**
> I'm sorry, but it seems to me that you may be being willfully pedantic about this (if not, I apologize). Look at this tutorial, as just one example of what I'm talking about: [https://wiki.archlinux.org/index.php/Change_username](https://wiki.archlinux.org/index.php/Change_username)

The '#' there means that the command should be run as root. Have you honestly never seen this before? Writing a command in this way in a tutorial, so as to indicate that the command should be run as a user with administrative privileges, is a pretty standard convention, and it seems to be exactly what is going on in the context of what the OP is referring to.

That said, yes, if a command is actually typed out by the user with a '#' before it (e.g., in a shell script, or at the command line), then it is a comment (assuming we're discussing Unix-style shells). But in terms of helping the OP actually understand what he is currently looking at, the present case looks like a case where he is being instructed to run a command as the root user.
I am not being pedantic. In 14 years as a linux user, I have never seen this syntax used to communicate running a command as root. It has never been used in any texts or tutorials I have run across, and based on all the training I've received over the years, it isn't correct. If this is some bizarre and esoteric method of communicating "run as root", I apologize. I've been a linux sysadmin for almost 9 years and have never encountered this "convention" before.

---

### Post by jrog on 2012-09-20
> **qamelian said:**
> I am not being pedantic. In 14 years as a linux user, I have never seen this syntax used to communicate running a command as root. It has never been used in any texts or tutorials I have run across, and based on all the training I've received over the years, it isn't correct. If this is some bizarre and esoteric method of communicating "run as root", I apologize. I've been a linux sysadmin for almost 9 years and have never encountered this "convention" before.
The convention is based on the fact that, typically, when you log in as the root user, your prompt ends with '#'. Typically, when you are not logged in as the root user, your prompt ends with '$'. So, people write texts/tutorials to indicate this, like so (they leave out the rest of the prompt because the rest of the prompt varies greatly from system to system):

> 
1. Switch to the root user:

```
$ su -
```2. Search for files ending in '.conf':

```
# find / -iname *.conf
```I can't tell what you think is incorrect about this. It is a simple way of indicating to users who are learning the system that the prompt will be different when they switch to the root user. 

It *would* be incorrect if the text/tutorial said something like, "You must type the '#' at the beginning of the line before typing the command," because in *that* case the '#' would make the command a comment. But the tutorials don't say this. Often, but not always, they do say that you shouldn't type that character, because it simply represents the root user's prompt. They don't always say this, though, because it is a pretty standard convention. I am very surprised you haven't seen it, but, in that case, I apologize for suggesting that you were being pedantic.

EDIT: And, in any case, we're starting to derail the thread, so I apologize for that, too. I still think that in the OP's case, he is likely reading something that is intended to indicate that the command should be run as a user with administrative privileges. I'll wait to see whether the OP can chime in to confirm this.

---

### Post by malspa on 2012-09-20
Some examples in this tutorial:

[http://www.thegeekstuff.com/2010/09/linux-fdisk/](http://www.thegeekstuff.com/2010/09/linux-fdisk/)

---

