---
title: "What is the Terminal command to delete a directory?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by SammySpencer on 2008-06-07
Hey, folks.

As you can tell, I am totally new to Linux.

I was trying to use Clonezilla to make an image of my Ubuntu build, and didn't realize that I had created the image on the same hard drive I was imaging.  So, I filled up my drive with the image file.  (Queue laughter now.)

What I am trying to do is delete the directory in which the image was created, since the hard drive is full.  I don't know what the Terminal command is to delete a directory.  I do know that I will need to use the "superuser" paramater ("sudu") to execute the command.  However, I don't seem to be successfully executing the command.  (I would have thought that the command "delete" or "delete directory would be it, but Terminal keeps giving me the message "command not found".)

Could someone offer a total newbie what this command is?

Thank you very much!


Sincerely,

Sammy Spencer

---

### Post by okey666 on 2008-06-07
You would want:
```
sudo rm -r (put your directory here)
```
:)
 I think that is correct.

---

### Post by Monicker on 2008-06-07
sudo rmdir /dir, if the directory is empty.  sudo rm -rf /dir, if the direcotry is not empty.

Be certain before using the latter option, as it will delete all subdirectories and files.

---

### Post by y-lee on 2008-06-07
It is easier for a "newbie" to use Nautilus, the command below will open it as super user and you should be able to delete what ya want

```
gksudo nautilus
```

---

### Post by SammySpencer on 2008-06-07
That was it!

Thank you so much, guys!  You really saved my day!  You guys rock!

Have a great weekend!


Sincerely,

Sammy Spencer

---

### Post by xeth_delta on 2008-06-07
> **Monicker said:**
> sudo rmdir /dir, if the directory is empty.  sudo rm -rf /dir, if the direcotry is not empty.

Be certain before using the latter option, as it will delete all subdirectories and files.

I really hate to intrude like this, Monicker. It is not my intention to annoy, but I think an observation is very important.

If you prepend the "/" to the directory name, rm will start erasing directly directories immediately under / (root directory) in the hierarchy. This, together with "sudo" and "-rf" has potentially harmfull consequences if the user does not completely understand what he/she is doing.

I believe a more descriptive way to express it would be:
If you have writing permisions to the files and directories in question(usually owned by the respective user):
```
rm -r path_to_directory
```
And if you need administrative privileges to alter them:
```
sudo rm -r path_to_directory
```

To the OP:
Please be *very very* careful when using these commands (especially the last one).
The "-r" means recursive under subdirectories. The extra "-f" option means "ask no questions" for this command, use with care.

As an additinal note, practically all commands have a manual you can consult, if you want to learn more. To access them:
```
man command_name
```
To search for a word, once reading it, press "/", type the word and press Enter. to quit, press "q".

Good luck, and don't hesitate to ask if you need further help.

---

### Post by Monicker on 2008-06-07
> **xeth_delta said:**
> I really hate to intrude like this, Monicker. It is not my intention to annoy, but I think an observation is very important.

If you prepend the "/" to the directory name, rm will start erasing directly directories immediately under / (root directory) in the hierarchy. This, together with "sudo" and "-rf" has potentially harmfull consequences if the user does not completely understand what he/she is doing.
.

I do not see your point.  I agree that one should be as precise as possible in using paths to directories and files, but the way I stated it should be perfectly acceptable.

I did not say to use "sudo rm -rf / dir".  An extra space would have made a huge difference in the results in the command.

Doing "sudo rm -rf /dir" would only remove "/dir" and all of its subdirectories.  It would not start at "/" and remove everything below it.

---

### Post by xeth_delta on 2008-06-07
> **Monicker said:**
> I do not see your point.  I agree that one should be as precise as possible in using paths to directories and files, but the way I stated it should be perfectly acceptable.

I did not say to use "sudo rm -rf / dir".  An extra space would have made a huge difference in the results in the command.

Doing "sudo rm -rf /dir" would only remove "/dir" and all of its subdirectories.  It would not start at "/" and remove everything below it.

Sorry for not making my point clear. What I meant, is that I do not see the necesity of prepending "/" to the directory name, as the path would implicitly englobed in the directory name. I know you did not mean "/ dir", but for a beginner, like the OP, that might create confusion.

It's probably a matter of semantics, but I just wanted to make that observation. I hope we can finish now this small argument :)

---

### Post by N.N. on 2008-06-07
[QUOTE=Monicker]Doing "sudo rm -rf /dir" would only remove "/dir" and all of its subdirectories.  It would not start at "/" and remove everything below it.[/QUOTE]

That wasn't what he said. He said the following:

[QUOTE=xeth_delta]If you prepend the "/" to the directory name, rm will start erasing directly directories **immediately under / (root directory) in the hierarchy**. This, together with "sudo" and "-rf" has potentially harmfull consequences if the user does not completely understand what he/she is doing.[/QUOTE]

That is correct. Imagine having a directory called 'tmp' in your home directory. Following your instructions, one would remove the 'tmp' directory in the root directory instead of the one in the home directory. As xeth_delta said, that could potentially have harmful consequences for an unsuspecting user.

---

### Post by Monicker on 2008-06-07
> **N.N. said:**
> That wasn't what he said. He said the following:



That is correct. Imagine having a directory called 'tmp' in your home directory. Following your instructions, one would remove the 'tmp' directory in the root directory instead of the one in the home directory. As xeth_delta said, that could potentially have harmful consequences for an unsuspecting user.

Okay, Now we are just quibbling over semantics.  :)

The OP did not state the location of the directory which he was trying to remove.  For all we know, it could have been /image that he wanted to remove.  I believe he understood what I meant.

/dir was clearly a generic example of a directory name.  In my mind it is a given that you should replace it with the name of the actual directory that he had in mind.  Technically speaking, a full path name will always start with a /, even if its /home/username/tmp.  That being said, in the future I will ask for clarification of the what directory they have in mind.

---

### Post by xeth_delta on 2008-06-07
> **Monicker said:**
> Okay, Now we are just quibbling over semantics.  :)

The OP did not state the location of the directory which he was trying to remove.  For all we know, it could have been /image that he wanted to remove.  I believe he understood what I meant.

/dir was clearly a generic example of a directory name.  In my mind it is a given that you should replace it with the name of the actual directory that he had in mind.  Technically speaking, a full path name will always start with a /, even if its /home/username/tmp.  That being said, in the future I will ask for clarification of the what directory they have in mind.

Yeah, I think he understood, he solved the problem, after all. I agree we're going off-topic now and discussing semantics :p

In any case, I believe we all agree a path includes everything, starting from the "/" coming from the root directory.

To the OP, please mark the thread as solved, if you managed to do what you needed.

---

