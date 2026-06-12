---
title: "Python get terminal user prompt"
date: 2013-09-23
forum: Programming Talk
---

### Post by evamvid on 2013-09-23
Hey Everybody, 

I'm trying to make a python script of the xkcd "Make me a Sandwich Comic". I need a way for python to be able to detect and replicate the user's prompt (User@Ubuntu:~$) *at the time they run the script*. So, if the user has cd'd into /dir/ect/ory/, their prompt will be "User@Ubuntu~/dir/ect/ory/:~$" .  I need to be able to grab that in python and output it at the beginning of the line, so it just looks like another terminal line. This assumes the user runs the script using the command line, but if they just click on it, it should just output "User@Ubuntu:~$" in a new terminal.

Thanks!
evamvid

---

### Post by evamvid on 2013-09-24
Also, I need help closing the terminal window after the script finishes, so it doesn't just leave it lying around. 

Thanks!

---

### Post by ofnuts on 2013-09-24
[https://help.ubuntu.com/community/CustomizingBashPrompt](https://help.ubuntu.com/community/CustomizingBashPrompt)

Good luck :)

(didn't a find any way to obtain the current prompt in a file.... but I have missed something)

---

### Post by Bachstelze on 2013-09-24
And why exactly do you want to do this in *Python*? Just do it in Bash...

---

### Post by evamvid on 2013-09-24
I thought it would be a fun Python exercise.

I am planning to learn bash, but I wanted to do this one in python.

---

