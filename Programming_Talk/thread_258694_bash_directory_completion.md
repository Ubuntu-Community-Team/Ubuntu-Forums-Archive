---
title: "bash directory completion"
date: 2006-09-16
forum: Programming Talk
---

### Post by mobin on 2006-09-16
In an sh shell, I have an environment variable say APACHE=/etc/apache2/

If I type "cd $APACHE/" then tab, it will complete to "cd /etc/apache2"

However if I try the same thing in a bash shell it won't complete. Instead it just gives "cd \$APACHE".

The problem seems to be with using the cd command. If I type "$APACHE" and then tab, it completes to "/etc/apache2/" as expected.

Is there a way of setting environment varaibles in BASH which I'm missing. I'd be greatful for any help. Thanks.

---

### Post by nereid on 2006-09-16
Sorry, but I do not understand what you want. Why don't you press enter after entering "cd $APACHE", this would take you into the apache directory.

---

### Post by mobin on 2006-09-16
No it doesn't take you into the correct directory. You get a no file or directory error.

Plus this is a shortcut so after tabbing I'd want to go further down the directry structure.

Eg. "cd $APACHE" tab would give "cd /etc/apache2/" then I could go further down from there.

---

### Post by nereid on 2006-09-16
Strange, I just tested this and a "cd $APACHE" changed the directory without a hitch. But I have no idea how to resolve the quoting problem.

---

### Post by cwaldbieser on 2006-09-17
> **mobin said:**
> In an sh shell, I have an environment variable say APACHE=/etc/apache2/

If I type "cd $APACHE/" then tab, it will complete to "cd /etc/apache2"

However if I try the same thing in a bash shell it won't complete. Instead it just gives "cd \$APACHE".

The problem seems to be with using the cd command. If I type "$APACHE" and then tab, it completes to "/etc/apache2/" as expected.

Is there a way of setting environment varaibles in BASH which I'm missing. I'd be greatful for any help. Thanks.

In bash, the behavior is controlled by the "complete" command.  Try "help complete" for the syntax.  Possibly you just need to add another completion rule.

---

### Post by mobin on 2006-09-17
Thanks for your replies. I'll try the suggestions out.

---

