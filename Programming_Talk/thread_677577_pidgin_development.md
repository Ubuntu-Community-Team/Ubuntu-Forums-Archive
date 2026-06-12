---
title: "pidgin development"
date: 2008-01-24
forum: Programming Talk
---

### Post by scamper_22 on 2008-01-24
Hi all,

I have the standard pidgin installed from the repo (2.2.1).
I decided to try some development so I downloaded the source of pidgin (2.3.1 from the pidgin website).
I then did a ./configure, make, sudo make install

Now, my original pidin does not launch.  I think I might have messed this up.  
My intention was to keep the pidgin from the repo and just use the source for development and playing around.

Before I maybe screw things up more:
anyone know how I can restore my repository pidgin
and what was my mistake in terms of development here?  Why did a development version screw up my repo version?

Thanks for the help anyone.

---

### Post by scamper_22 on 2008-01-24
sorry, forgot to mention.  If I run the development pidgin, it doesn't work either.

/usr/local/bin$ ./pidgin 
./pidgin: symbol lookup error: ./pidgin: undefined symbol: purple_account_get_current_error

i googled a bit and other people seem to have problems with this as well.

---

### Post by scamper_22 on 2008-01-25
okay, looks like the repo version is not screwed up.

If I launch it from /usr/bin, I get the original 2.2.1 version.  Which is good.

Sorry, I seem to be solving this on my own... :P

So if I type pidgin at a prompt, how does it know which version to get.
How does know to try from /usr/local/bin as opposed to /usr/bin ?

Is it just the search order...so to fix this, I just rename the one in /usr/local/bin and then I can use it for development...once I solve it's error?

Thanks,

Y

---

### Post by scamper_22 on 2008-01-25
ahh, genius,  /usr/local/bin is first in the path.  excellent.

alright...so now we're down to finding out why the development version of pidgin doesn't want to work.  I've seen some notes that you have uninstall the repo version before the dev version will work.  that would not be very good...for what I want to do.

anyone done this before?

---

### Post by scamper_22 on 2008-01-25
Ok, I think i've got it.

doing ldd /usr/local/bin/pidgin
tells me that pidgin is using the libpurple from the repo version

How do I tell the lib loader to first check
/usr/local/lib ?

Is there a variable I can set to alter where it looks for libraries?
I don't mind setting this variable when I want to do 'development' and unsetting back to regular for normal operations?

Thanks,

Y

---

### Post by scamper_22 on 2008-01-25
bah, kind of ugly

but for now I just changed the sym link in /usr/lib/libpurple.so.0 to point to the one in usr/local/lib.

seems to work fine...but kind of ugly.
wish there was a better way.

Y

---

### Post by seventhc on 2008-01-25
Good Luck :)

---

