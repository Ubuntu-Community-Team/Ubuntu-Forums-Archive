---
title: "Weird characters in newsposts. What to do?"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by gladgrind on 2012-11-13
When I download newsgroup posts using the Pan newsreader, all is well, and I see a subject like:

Subject: Re: E=mc² is incomplete


But when I run a little python script and download the same post using the nntp function, and look at it using gedit, I see:

Subject: =?Windows-1252?Q?Re:_E=3Dmc=B2_is_incomplete?=


There are lots of other weird things using the python script - things that should be apostrophes or quotes but show up as odd character combinations - something like =93 or =94 - I forget exactly what.

Is there something I can do, maybe some font I can add that will let gedit or python render these things correctly?

---

### Post by Impavidus on 2012-11-14
The line is most likely stored as:

Subject: =?Windows-1252?Q?Re:_E=3Dmc=B2_is_incomplete?=

Your newsreader knows how to convert that to

Subject: Re: E=mc² is incomplete

The problem is that the newsgroup doesn't allow modern character encodings, so it uses a workaround for any non-standard characters. The B2 and 93 things are part of escape sequences denoting the characters in the windows-1252 encoding. There must be a python module to convert this to a normal encoding (like the linux-native UTF-8). I'm sorry I can't tell you the name of the encoding used. Browsing wikipedia on character encodings might help.

---

