---
title: "What is the Regular Expression for this to block and allow?"
date: 2008-03-26
forum: Programming Talk
---

### Post by Zedrick on 2008-03-26
There are some flags I would like to have blocked,  and some flags I would like to allow, when a user tries adding a hostmask of *!*@* for any given hostmask to any of these flags.



The flags I am wanting to block are +vhHoOaqsirRftAF

There is also Flag +* to block aswell that adds all flags except Flag +b and +F

- when a user tries to add a hostmask to any one of these blocked flags to block it.



Flags I am wanting to allow are +Vb

- when a user adds a hostmask to any one of these allowed flags to allow it.



The command to add Flags using hostmasks

/msg ChanServ flags #channel *!*@* +abcd
/msg ChanServ flags #channel *!*@* +*

/chanserv flags #channel *!*@* +abcd
/chanserv flags #channel *!*@* +*
/cs

`flags *!*@* +abcd
`flags *!*@* +*

ChanServ flags *!*@* +abcd
ChanServ flags *!*@* +*



What is the Regular Expression for this to block and allow these flags on hostmasks *!*@* ?

---

### Post by skeeterbug on 2008-03-26
Here is a sample anything except v and H. 

If you change the flag to +H, you will notice it isn't allowed. The regex negates v and H, with [^v|^H], you can obviously add others, as it isn't complete. The entire regex needs work, but it should give you and idea of where you need to go.

```

use strict;

my $string = "/msg ChanServe +Vb";

if($string =~ m/msg\sChanServe\s\+[^v|^H]/) {
 print "That flag is allowed!";
} else {
 print "That flag wasn't allowed";
}
```

If you wanted to do allow flags too, I suppose you could use groups (one being negated, one not). Hope that helps.

---

### Post by Zedrick on 2008-03-26
The Regular Expression I am wanting to do is done in a filter.conf file with the tag

```
<keyword pattern="^blah.*?$" reason="Dont blah!">
```

which is an example one.

sorry I did not post this tag of how the Regular Expression is done. -- sorry for that skeeterbug

and also block +* from being added to on hostmasks.

When a user adds a user to the blocked flags - it allows it.

only blocks and allows hostmasks of *!*@* for any given hostmask for any of these flags. - Case Sensitive with blocked v and allowed V

Probably only the flags to block +vhHoOaqsirRftAF,  and +*,  to have there in the keyword pattern tag,  which then allows the Flags +Vb to be used on hostmasks.

Regular Expressions is quite complex to get your head around.

---

### Post by Zedrick on 2008-03-27
something like this to block +vhHoOaqsirRftAF and block +* on *!*@*

and allow +Vb

```
<keyword pattern="*flags*+[^\*|^v|^h|^H|^o|^O|^a|^q|^s|^i|^r|^R|^f|^t|^A|^F$]*!*@*" reason="abcd">
```

how do I correct this for it to work?

---

### Post by baumgc on 2008-03-27
[IMG]http://imgs.xkcd.com/comics/regular_expressions.png[/IMG]

I can't help you.
Good luck though!

---

### Post by mssever on 2008-03-27
> **Zedrick said:**
> something like this to block +vhHoOaqsirRftAF and block +* on *!*@*

and allow +Vb

```
<keyword pattern="*flags*+[^\*|^v|^h|^H|^o|^O|^a|^q|^s|^i|^r|^R|^f|^t|^A|^F$]*!*@*" reason="abcd">
```how do I correct this for it to work?

You mean, something like this?
```
<keyword pattern="\*flags\*\+[Vb]+\*!\*@\*" reason="abcd">
```Or, if you need an exclusion list instead of an inclusion list, ```
<keyword pattern="\*flags\*\+[^vhHoOaqsirRftAF*]+\*!\*@\*" reason="abcd">
```I've had to make some assumptions when it comes to escaping since I don't know the syntax rules of IRC.

---

### Post by Zedrick on 2008-03-28
This is for IRC on Atheme Services,  that you can add hostmasks to the Channel Access List. -- anyone who happens to be on a hostmask will get access to the channel.  Wanting to disable adding of hostmasks.



I had it round the wrong way sorry with the hostmasks after the flags. -- hostmasks before the flags.

The Regular Expressions didn't work sorry - on both ways.



```
<keyword pattern="\*flags*\*!\*@\*\+[Vb]" reason="abcd">


<keyword pattern="\*flags*\*!\*@\*\+[^vhHoOaqsirRftAF*]" reason="abcd">
```



private message to ChanServ

/msg ChanServ flags #channel *!*@* +abcd
/msg ChanServ flags #channel *!*@* +*

/chanserv flags #channel *!*@* +abcd
/chanserv flags #channel *!*@* +*
/cs



commands done inside the channel

`flags *!*@* +abcd
`flags *!*@* +*

ChanServ flags *!*@* +abcd
ChanServ flags *!*@* +*



*flags*!*@*+abcd

- covers both the private message commands and inside the channel commands.

---

### Post by mssever on 2008-03-28
> **Zedrick said:**
> /msg ChanServ flags #channel *!*@* +abcd
/msg ChanServ flags #channel *!*@* +*

/chanserv flags #channel *!*@* +abcd
/chanserv flags #channel *!*@* +*
/cs



commands done inside the channel

`flags *!*@* +abcd
`flags *!*@* +*

ChanServ flags *!*@* +abcd
ChanServ flags *!*@* +*



*flags*!*@*+abcd

- covers both the private message commands and inside the channel commands.

Thanks for the additional info. I still don't know whether you need positive or negative filtering. Based on the samples you gave, one of these should get you started:

```
flags(\s+#[a-zA-Z]+)?\s+\*!\*@\*\s+\+[^vhHoOaqsirRftAF*]
flags(\s+#[a-zA-Z]+)?\s+\*!\*@\*\s+\+[Vb]
``` Since I obviously can't test these, you might have to tweak them a bit to make them work, but they should give you the general idea. If that regex implementation doesn't understand \s, you can replace it with [ \t]. So \s+ becomes [ \t]+ and so forth.

---

### Post by Zedrick on 2008-03-29
Both the block and allow didn't work sorry. -- with both \s+ and [ \t]+

The Regular Expression on the flags to block would be better.

What about having *flags*!*@*+flags - to block any of the given flags with, and +* to block aswell that adds all flags except for +b and +F,  to cover both private message commands with the #channel name in it, and the in-channel commands without the #channel name.

---

### Post by mssever on 2008-03-29
> **Zedrick said:**
> Both the block and allow didn't work sorry. -- with both \s+ and [ \t]+

The Regular Expression on the flags to block would be better.

What about having *flags*!*@*+flags - to block any of the given flags with, and +* to block aswell that adds all flags except for +b and +F,  to cover both private message commands with the #channel name in it, and the in-channel commands without the #channel name.

Without being able to test it, I don't think there's much more I can do. I suggest that you learn regex syntax yourself (give yourself plenty of time for the task), that way, you can adjust it and see what works.

---

