---
title: "Which tools to use to extract emails out of large file? (awk, regexp?)"
date: 2009-03-16
forum: Programming Talk
---

### Post by bighype on 2009-03-16
Hi all,

I have a database dump that my DB buy gave me and I'd like to extract all the emails out of it. Basically, emails are in a txt file that has a lot of 'garbage in it'. Emails are separated by spaces.

What I'd like to do is just extract emails, one per line, and get rid of all the other junk.

I use Ubuntu but I'm not sure what would be the way to go about it to make it automated (I have about 1000 emails to extract).

Someone told me to use awk and regexp but I have no idea how to do that.

Could someone help me please? THANKS!

Mel

---

### Post by ghostdog74 on 2009-03-16
practically, most prog languages allow you to do that. what languages do you know? 
```

# awk '{for(i=1;i<=NF;i++) { if ($(i) ~ "@") print $i}}' file

```
if you don't know something, look it up in the documentation, learn and practice. don't just say "don't know", "no idea". Look at my sig for awk resources. have fun

---

### Post by bighype on 2009-03-16
> **ghostdog74 said:**
> practically, most prog languages allow you to do that. what languages do you know? 
```

# awk '{for(i=1;i<=NF;i++) { if ($(i) ~ "@") print $i}}' file

```
if you don't know something, look it up in the documentation, learn and practice. don't just say "don't know", "no idea". Look at my sig for awk resources. have fun

Wow... that worked perfectly!!! THANK YOU SO MUCH :) I need to learn this tool.

---

### Post by ghostdog74 on 2009-03-16
take note that that would not validate the emails for you. it will only show you strings with @ in it, even though they might sometimes not contain email like syntax.

---

