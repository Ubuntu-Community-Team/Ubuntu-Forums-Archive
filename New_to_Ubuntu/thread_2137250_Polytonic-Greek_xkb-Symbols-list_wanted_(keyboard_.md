---
title: "Polytonic-Greek xkb-Symbols-list wanted (keyboard layout)"
date: 2013-04-20
forum: New to Ubuntu
---

### Post by LatGrc on 2013-04-20
Dear Forum-members,

I was quite content with [this old thread here]("http://ubuntuforums.org/showthread.php?t=188761") when I created a keyboard layout for continually writing in Latin with macrons and occasionally with brevia, too.

But as I also would like to write in old greek, that is with all its "polytonic symbol extensions" (dasia, oxia, varia, ypogegrammeni,  perispomeni) which are very often combined, I have come to limits[SUP]1[/SUP]:

"dead_acute" may work - "dead_U1FCD" (= dead &#8157; ) does not.

The linked thread above contains a "symbols_list.txt", listing the "codenames" in xkb or X11 with their Unicode signs and descriptions as follows:
> Greek_ALPHAaccent             0x07a1  /* U+0386 GREEK CAPITAL LETTER ALPHA WITH TONOS */
Unfortunately, the 'Greek'-section of this file does note contain the codenames for polytonic Greek.

so I ask you:
[LIST=1]
[*]Where could I find a new "symbols_list"-file that contains the required "codenames"? 
[*]If such codenames for Greek polytonic signs do not exist at this time - how could I create them(the Alphanumerical code int the middle of the quoted line could be a hint)?
[*]If this is just the wrong place, could you show me the appropriate forum :) ? 
[/LIST]

Thank you for your support :)

I know that my issue is rather special, but as I am new to these Forums I did not see an appropriate place :)

LatGrc

[SUP]1[/SUP]The "polytonic Greek"-layout offered in Precised Pangoline does not contain combined signes as the example &#8157; (dasia with varia) showed above.

---

### Post by LatGrc on 2013-04-21
Hello,

I tried to find this definition file in the X11 and X11/xkb directories - but so far I was not able to find it - could any moderator or Admin move my thread to General Help? I guess this is not a typical "Absolute Beginner"-problem.

Good bye,

LatGrc

---

### Post by LatGrc on 2013-04-21
Hello :)

I have found the file(Precise Pangolin = 12.04): ```
/usr/include/X11/keysymdef.h
``` 

This the good news! The bad news are twofold:

1. there are now "mnemonic names" like ```
dead_dasia
``` for the combined diacritics I need.
2. the codes like ```
0x07a1
``` do not refer directly to Unicode signs - some where hidden is another mapping file: I've made id into one more deeper level in these dungeons :)

I hope others' problems will be solved at this stage with "keysymdef.h" :)

As nobody seems to know something about this matter in this place I will start a new, appropriately titled post in "General Help" *leaving a link to it here:*

[http://ubuntuforums.org/showthread.php?t=2137652&p=12612670#post12612670](http://ubuntuforums.org/showthread.php?t=2137652&p=12612670#post12612670)

Forgive for this cross post: I beg everybody to answere to the new thread in "General help"!

Thanks for reading,

LatGrc

---

### Post by LatGrc on 2013-08-01
Hello everybody,

I've found and easier solution for this myself, just a bit later. I gave up hunting the "0xfe53" codes and *simply reused some dead key codenames* originally listed for latin alphabets - e.g. "dead_caron" to write &#269; š &#543; etc. 
 
0. I recommend you (as you are probably newbies like me :) ) to make backup copies of all files to be changed; to make an other set of copies for working on them, in order not work in the "living system". Simply copy the updated files into the respective system folders to overwrite the old ones. Here we go:

1.  I looked up the existing "dead_..." codenames in 
```
/usr/include/X11/keysymdef.h
``` 
(Attention: it's of no use to use aliases of a code name you already use, e.g. 
```
#define XK_dead_tilde                    0xfe53
#define XK_dead_perispomeni              0xfe53  /* alias for dead_tilde */
```
But don't worry, there are plenty, about thirty codes like "0xfe50" asigned to the "dead_..."-codenames you need to 'activate' the xkb-deadkey function).

2. I made a "list of character wishes" where I sketched the places of the dead keys I need on my keyboard, noting the disposable dead key names to the intented diacritics.

3. .XCompose (sic! with "." in the beginning!) uses those dead key names to "invoke" actual charakters. All I did was inserting lines which combined the reused dead key names with the Greek character names and, of course the very Unicode Character itself in the end, looking like this:
```
<dead_circumflex> <Greek_alpha> : "&#7942;"
<dead_belowcircumflex> <Greek_alpha> : "&#7943;"
<dead_voiced_sound> <Greek_alpha> : "&#8070;"
<dead_semivoiced_sound> <Greek_alpha> : "&#8071;"
...
```

Then the capital ones:
```
<dead_circumflex> <Greek_ALPHA> : "&#7950;"
<dead_belowcircumflex> <Greek_ALPHA> : "&#7951;"
<dead_voiced_sound> <Greek_ALPHA> : "&#8078;"
<dead_semivoiced_sound> <Greek_ALPHA> : "&#8079;"
...
```
then with epsilon, Epsilon and so on.

It is some "hand work" (I wrote a single file for &#945;/A then copied it to a new one for &#949;/E etc.). I took the Unicode characters from the Greek table of Ubuntu's preinstalled Character table.

3. I rewrote the file
```
the file /usr/share/X11/xkb/symbols/gr
```
which assigns the death key/character names to the actual keys, as follows:
```
key <AC01> { [           Greek_alpha,    Greek_ALPHA, a ] }; // &#945; &#913; a
```
"AC01" is the Name of the key, the brackets contain the codenames by the simple order "simple key", "key with shift", "key with AltGr", "key with AltGr + shift"(the latter two can be left out).
A line with the reused dead key codenames looks like this:
```
key <AC11> { [ dead_psili, dead_dasia, dead_caron, dead_cedilla  ] }; // ` &#788;
```
"AC11" is the name of the Ü-key of the German keyboard. In [this thread]("http://ubuntuforums.org/showthread.php?t=188761") you will find an image that shows all names of the keys written on them :) The author also kindly explanes the system behind "A C 11". Quite an easy one :) Thank you designers :)

That's all :)

For my keyboard I chose approximately the mapping of Windows' Greek Polytonic. It is fairly comfortable now (I'm glad to have found and email partner in the meantime :) ). NOTE: I have attached my "Extension" the .XCompose file and my version of the ...xkb/symbols/gr file( the latter is a bit chaotic :oops: : I used both the "basic" and the "polytonic" parts. But it works as long as you only use "Greek polytonic".

I hope to help somebody with the same issue and the same zest for productive writing in Old Greek :)

Bye,

LatGrc

---

### Post by LatGrc on 2013-08-01
Sorry, forgot the attachments :) Here they are. NOTE: I had to rename them into ".txt" files, because the upload system of the Ubuntu forums does not find them without extension. Please remove the ".txt" before implementing! Thanks for reading :)

---

