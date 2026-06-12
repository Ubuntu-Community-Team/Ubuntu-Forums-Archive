---
title: "How do I run sudo -s then apt-get update then apt-get dist-upgrade all in one command"
date: 2017-03-18
forum: New to Ubuntu
---

### Post by xplisit2017 on 2017-03-18
Sorry I am a linux noob.
Sorry if this has been answered in another post please merge them if so.
I know how to install linux and run basic commands like sudo and apt-get update but as the title says i want to type sudo -s, my password, apt-get update, and apt-get dist-upgrade all in one line and run. Is there a way to do this? If so how do I do this and also how do I make this into a script so that i can run as a batch file(windows terminoligy) so i dont have to type all this in every time i want to do this.

---

### Post by yancek on 2017-03-18
You should be able to do that by using the ampersand, i.e:  sudo -s  apt-get update && apt-get dist-upgrade
I haven 't tested this but I would expect you would be prompted for your password first.  Put the command in a bash script and make it executable.

---

### Post by oldos2er on 2017-03-18
I use the alias *up* with this line in ~/.bashrc ```
alias up='sudo apt update && sudo apt full-upgrade'
```

---

### Post by vasa1 on 2017-03-18
It looks like OP wants to include the password in the script (or alias).

---

### Post by vasa1 on 2017-03-18
> **xplisit2017 said:**
> ... i want to type sudo -s, my password, apt-get update, and apt-get dist-upgrade all in one line and run ...
Wouldn't that be *[FONT=Courier New]sudo -S[/FONT]*? And some people feel that's not a really good idea because it involves storing your password as plain text making it easier for someone to harm you.

Anyway, there's no real need for a script in this case. An alias would work just fine.

---

### Post by oldos2er on 2017-03-18
> **vasa1 said:**
> It looks like OP wants to include the password in the script (or alias).

That seems a bit dangerous, which is why I ignored it.

---

### Post by pauljw on 2017-03-19
> **xplisit2017 said:**
> Sorry I am a linux noob.
Sorry if this has been answered in another post please merge them if so.
I know how to install linux and run basic commands like sudo and apt-get update but as the title says i want to type sudo -s, my password, apt-get update, and apt-get dist-upgrade all in one line and run. Is there a way to do this? If so how do I do this and also how do I make this into a script so that i can run as a batch file(windows terminoligy) so i dont have to type all this in every time i want to do this.

One thing no one has mentioned is if you aren't doing lots of things in the terminal that command will be within a few up arrow key presses in the bash history file.  Just open the terminal, press the up arrow key till you see that command and press enter, enter your password and press enter again and it will run.

---

### Post by vasa1 on 2017-03-19
> **pauljw said:**
> One thing no one has mentioned ...
Very true! But that wasn't OP's question :)

---

