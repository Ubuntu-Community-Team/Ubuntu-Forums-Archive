---
title: "apt-get command question"
date: 2006-04-05
forum: Repositories &amp; Backports
---

### Post by nrwilk on 2006-04-05
I'm writing a script to make installing a piece of software easier.

The script downloads some dependencies from the repositories.

But, I noticed that if one apt-gets a bunch of packages and one isn't available (such as one which is located in a repo which isn't activated in one's sources.list), instead of continuing without that package, the whole thing bails.  ( I hate this behavior ) :mad: 

Is there some way I can check to make sure that everything is correctly installed, and make the script exit if not.

I looked through the apt-get man page, and it says that it will return "decimal 100" on errors.  How can I utilize this exit code in the script?  Will the scenario which I described trip it as an error?

Is there a way to do this?

Thanks for any help! :)

---

### Post by nrwilk on 2006-04-05
Nevermind.  I figured it out.

Google is your friend. :p  :D

---

