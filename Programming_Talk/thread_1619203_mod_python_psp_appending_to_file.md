---
title: "mod_python psp appending to file"
date: 2010-11-11
forum: Programming Talk
---

### Post by Crazedpsyc on 2010-11-11
I am trying to make a simple chat page on my local website. I was going to do it by having a simple html form like this
```
<form name="chat" method="post" action="addchat.psp">
<input type="text" name="chat"></input>
<input type="button" value="Chat"></input>
</form>
```but when I try to do (this is in my addchat.psp file)
```
chatxt = open('/var/www/chatroom/chat.txt', 'a')
chatxt.write(form['chat'])
```I get error 13, permission denied to chat.txt.
I tried putting chat.txt in both my home folder and /tmp/ but it still gave the same error.
How can I get across this? And please don't tell me to stop using mod_python. I like it.
If I can somehow save the chat text to a cookie, that would be okay

Thanks in advance guys!

---

### Post by Crazedpsyc on 2010-11-12
Anybody? I tried chowning  and chgrping the chat.txt file to www-data but it still didn't work

---

### Post by Crazedpsyc on 2010-11-13
Some progress, then a degress. I allowed apache to write to the file by running ```
chmod a+w chat.txt
``` and that sort of worked. Then I noticed apache2 was using 25 percent of my CPU power (which is a pretty big amount for me) and taht the chat.txt file was growing at a rate of several megabytes per second. it wrote a bunch of nonsense repetetive code to the file. I fixed this issue and now it writes the correct line to the file (once) but when it gets to the line "from req import utils) which I use to redirect back to the index page it says "no module named req". any idea why? it worked before

---

### Post by Crazedpsyc on 2010-11-15
Solved

---

