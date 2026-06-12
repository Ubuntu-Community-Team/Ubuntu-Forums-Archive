---
title: "An easy one: I can't use nano to write bash scripts!!"
date: 2006-06-09
forum: Programming Talk
---

### Post by ssalman on 2006-06-09
Hi, this post is probably overkill! :) read on to know why.

I'm not new to programming or scripting, but I am kind of new to Linux and completely n00b to bash scripting. Tried my first simple script two days ago, and had a very interesting [FONT=&quot][/FONT]problem, I solved it but I still don't understand the solution. can you help me figure this one out? ;)

my script included several lines like the below, all of which worked in bash CLI but didn't work in the bash script:
```
uname -n > dir/filename.log
```

The problem I found was that I was using nano as my editor, and it actually adds a invisible [^k] character at the end of the line, not sure if that's the [CR] character or not, but that's why I couldn't run my script. To solve it, I had to go into gedit, delete all the white-spaces between lines and then insert a [new line] between the lines.

I have read that nano can be used for scripting, what am I missing? and is nano really  not suitable for script coding?

---

### Post by nanotube on 2006-06-09
> **ssalman]Hi, this post is probably overkill! :) read on to know why.

I'm not new to programming or scripting, but I am kind of new to Linux and completely n00b to bash scripting. Tried my first simple script two days ago, and had a very interesting [FONT=&quot][/FONT]problem, I solved it but I still don't understand the solution. can you help me figure this one out?  said:**
>  character at the end of the line, not sure if that's the [CR] character or not, but that's why I couldn't run my script. To solve it, I had to go into gedit, delete all the white-spaces between lines and then insert a [new line] between the lines.

I have read that nano can be used for scripting, what am I missing? and is nano really  not suitable for script coding?
that's really strange. doesn't do anything like that for me. try looking around in the options/help for some settings?

---

### Post by ssalman on 2006-06-09
[quote=nanotube]that's really strange. doesn't do anything like that for me. try looking around in the options/help for some settings?[/quote]

So I take it that nano should work fine, and you have used it before for writing scripts? I guess I'll have to check it one more time, maybe I'm doing something wrong.:-s

---

### Post by nanotube on 2006-06-09
[QUOTE=ssalman]So I take it that nano should work fine, and you have used it before for writing scripts? I guess I'll have to check it one more time, maybe I'm doing something wrong.:-s[/QUOTE]

yes, i have used it to write scripts, and still do... :)

---

### Post by wmcbrine on 2006-06-10
^K is not the CR character (^M is), and nano should not be adding anything extraneous to the line endings, and doesn't for me. But it does have the *ability* to create CRLF- or CR-delimited files (which it labels "DOS Format" and "Mac Format", respectively), if you intentionally save them that way. It should default to LF; but maybe there's an option to change that? (Edit: Doesn't seem to be.) But since ^K isn't CR anyway, I don't know what the deal is.

---

