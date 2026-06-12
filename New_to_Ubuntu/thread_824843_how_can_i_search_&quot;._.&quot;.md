---
title: "how can i search &quot;. ./&quot;"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by sturmey on 2008-06-10
so I tried to search for an answer about what the dot space dot slash" does on the command line, but I can't get any results.

I recently took over responsibility for our network and have to do some cleanup on a few things left over from the previous admin. The how to docs I've found on the web are mostly written for ppl who have been doing linux for the past 10+ years and kinda suck. I've been getting strange errors that no one has listed, which I now discovered are ```
. ./vars
```
not```
../vars
```

yeah I couldn't tell the difference. So my question really is, what does the "dot space dot slash" do? I already figured out that "dot slash" will run the script, (although I'm not sure why I can't just run it directly the way I could in DOS, but apparently there is some kind of security issue? I have no idea how that helps, but oh well)

Sturmey

---

### Post by KingTermite on 2008-06-10
more information.

Where are you seeing this for starters?
What errors?

My first thought is it could be referring to two seperate directories (seperated by a space).
"." and "./vars"

---

### Post by sdennie on 2008-06-10
The behavior of ". ./" will depend on the program you are running.  In some programs it will consider "." to be a source directory and "./" to be a destination directory (for example, cp, mv, etc).  In other programs it will consider both "." and "./" to be a list of paths to use (for example, find).

Edit:
And in other programs it's simply not valid or the second argument is ignored (for example, cd).

---

### Post by sturmey on 2008-06-10
In this case I'm dealing with openvpn. the instructions for revoking certificates are:```
. ./vars
./revoke-full client2
```

running ./vars didn't work obviously, and putting two dots together gave me errors. Only when there was a space, which took 3 days to figure out, did it work. I'd like to know what it does, as I've worked with linux for several years and never come across that particular style of command.

for reference you can check: openvpn.net/howto.html#revoke

---

