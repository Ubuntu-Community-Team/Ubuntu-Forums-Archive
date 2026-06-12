---
title: "Can't compile lxpanel"
date: 2010-07-09
forum: Programming Talk
---

### Post by oakgrove on 2010-07-09
I'm running Ubuntu 10.04 and I'm trying to compile lxpanel with a slight adjustment but everytime I do ./configure and make, it errors out with this:```


batt.c:98: error: ‘alarm’ redeclared as different kind of symbol
/usr/include/unistd.h:429: note: previous declaration of ‘alarm’ was here
batt.c: In function ‘alarmProcess’:
batt.c:109: warning: ignoring return value of ‘system’, declared with attribute warn_unused_result
make[4]: *** [batt.lo] Error 1
make[4]: Leaving directory `/media/250Gig/nate/new_programs/source/lxpanel-0.5.5/src/plugins/batt'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/media/250Gig/nate/new_programs/source/lxpanel-0.5.5/src/plugins'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/media/250Gig/nate/new_programs/source/lxpanel-0.5.5/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/250Gig/nate/new_programs/source/lxpanel-0.5.5'
make: *** [all] Error 2

```

I've tried several different release numbers of lxpanel both from the repository and the project's sourceforge page and I've tried it with and without patching all with the same result. I also made sure to compile and install menu-cache and lxmenu-data packages first but nothing seems to be working. Any help would be appreciated.

---

### Post by dwhitney67 on 2010-07-09
There's no way I plan to download the code you are attempting to modify, but I was able to duplicate the error you are getting with a few lines of code.

Here's my application:
```

#include <unistd.h>

unsigned int alarm;

int main() {}

```
When I try to compile the above, this is the error that is given:
```

gcc batt.c 
batt.c:3: error: &#8216;alarm&#8217; redeclared as different kind of symbol
/usr/include/unistd.h:401: note: previous declaration of &#8216;alarm&#8217; was here

```
Now, with this information, do you think you could resolve the issue your version of lxpanel is having?  Look at batt.c at line 98; perhaps you could post the code that is thereabout.


Hint:  First thing to do is determine why *alarm* is being re-declared in lxpanel.  If you added the new declaration, I suggest you come up with a different name for the variable.

---

### Post by oakgrove on 2010-07-09
Thank you very much for taking the time to reply.  Unfortunately, I'm way too much of a noob at C to be able to really fix this.  Python, maybe.  Strangely, I was able to compile the panel on 2 of my other computers without any problem at all.  I guess there's just something wrong with the install on this box somewhere.  It's been upgraded a few times so it's just probably getting stale.  I'm going to just wipe the whole thing and start over since I need to do the ata delete routine on the SSD anyway.  This is just the straw that broke the camel's back.  Again, thanks.

---

### Post by inductiveload on 2010-11-04
This is caused by a typedef for "alarm" in "unistd.h" colliding with a new type of "alarm" in "batt.c". You can fix this problem by renaming all instances of "alarm" in batt.c.

There is a patch submitted [here]("https://sourceforge.net/tracker/?func=detail&aid=3102612&group_id=180858&atid=894871") if you like.

---

