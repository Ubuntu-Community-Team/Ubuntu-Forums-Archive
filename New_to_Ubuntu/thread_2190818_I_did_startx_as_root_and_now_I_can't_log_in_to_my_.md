---
title: "I did startx as root and now I can't log in to my account."
date: 2013-11-29
forum: New to Ubuntu
---

### Post by ryanstoner333 on 2013-11-29
I ran sudo startx and my computer freaked out so I shut it down and when I turned it back on it didn't log me on automatically. When I put my password in it just goes black for a second then makes the drum sound and  puts me back to the log  in screen. Can someone tell me how to fix this?

---

### Post by sisco311 on 2013-11-29
Please check out: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

Make sure that all the config ( dot ) files in your home directory are owned by your user.

---

### Post by ryanstoner333 on 2013-11-29
How do I do that? 0.0

---

### Post by steeldriver on 2013-11-29
You should be able to log in to a text console via one of the virtual terminals (Ctrl-Alt-F1 thru F6). Then check the ownership on your .Xauthority and .ICEauthority files

```
ls -l ~/.{ICE,X}authority
```

If either one is owned by root instead of you, either change it back 

```
sudo chown *user*:*user* ~/.Xauthority
```

where *user* is replaced by your actual username or simply delete it (they get regenerated as required)

```
rm -f ~/.Xauthority
```

Changing ownership needs 'sudo' whereas deleting doesn't so is usually easier - but make sure you get the command exactly right so as not to delete anything else.

---

### Post by ryanstoner333 on 2013-11-29
> **sisco311 said:**
> Please check out: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

Make sure that all the config ( dot ) files in your home directory are owned by your user.
How do I do that?

---

### Post by ryanstoner333 on 2013-11-29
> **steeldriver said:**
> you should be able to log in to a text console via one of the virtual terminals (ctrl-alt-f1 thru f6). Then check the ownership on your .xauthority and .iceauthority files

```
ls -l ~/.{ice,x}authority
```

if either one is owned by root instead of you, either change it back 

```
sudo chown *user*:*user* ~/.xauthority
```

where *user* is replaced by your actual username or simply delete it (they get regenerated as required)

```
rm -f ~/.xauthority
```

changing ownership needs 'sudo' whereas deleting doesn't so is usually easier - but make sure you get the command exactly right so as not to delete anything else.

thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by apollothethird on 2013-11-29
> **ryanstoner333 said:**
> How do I do that?

Hi, Ryanstoner.

How do you do what?  There is lots of information in the link you just quoted.  We don't know which part of the text you're having problems with.

Will you give us the output of this command?  Please use CODE tags to make your output easy to read such as I'm doing below:

```

$ find ~/ -user root 2>/dev/null

```

Please run the command in a terminal window.  You can get a terminal window by:

(Hit) Ctrl-F2 > (type) gnome-terminal > (press) ENTER

 That key sequence will give you a terminal.  Type in the command quoted in the code below and give us the output.  From the output we can tell you which files are screwed up.
[INDENT][COLOR=#008000]edit:  I see there were new posts while I was typing my message and someone has helped you to resolve your issue.  Please consider contributing back to the community by marking this topic as Sovled.  This way someone else having a similar issue can easy find this resolution.[/COLOR][/INDENT]

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by kuiper2 on 2014-10-08
> **ryanstoner333 said:**
> thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou thankyou !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

I just now had this same problem and changing the ownership of Xauthority worked so I feel the need to say thanks to both of you. Also, I didnt know you could use {} for multiple words simultaneously like that. That was a neat thing to learn

---

