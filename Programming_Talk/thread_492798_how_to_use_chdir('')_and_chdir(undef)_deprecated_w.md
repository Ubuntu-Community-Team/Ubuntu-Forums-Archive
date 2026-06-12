---
title: "how to use chdir('') and chdir(undef) deprecated with Perl 5.8.8"
date: 2007-07-05
forum: Programming Talk
---

### Post by E5o on 2007-07-05
Greetings

I have been using a Perl script [bax]("http://www.smalltime.com/gene/bax.html") to do backups for years on my OSX box.

Please bear in mind, I am no programmer as such.

But when I try it on my linux box it gives me this error message:

```
chdir('') and chdir(undef) are deprecated
```

After some reading on Perl.org I get this:

Using chdir('') or chdir(undef) instead of explicit chdir() is doubtful. A failure (think chdir(some_function()) can lead into unintended chdir() to the home directory, therefore this behaviour is deprecated.

So, my question is: How can I use chdir(' ') the correct way in Perl 5.8.8?

Thank you

---

### Post by Mr. C. on 2007-07-05
The chdir command with a undef value would change directories to the running user's home directory.

Perhaps you want the home directory of the running user:

```
chdir ("$ENV{'HOME'}");
```

or place the name of correct home directory as a parameter, as in :

```
chdir ('/home/mydir');
```

MrC

---

### Post by E5o on 2007-07-09
Thank you for the reply.

I got an answer back from the author the other day. 

> replace this line near the top:
```
use Cwd;
```
with:
```
use Cwd qw(getcwd);
```

Then replace this line in make_backup:
```
my $cwd = cwd();
```
with:
```
my $cwd = getcwd();
```

I tried it and it worked.

Although I think this solution may be related to this particular script and not a universal solution. Anyway I good now.

Cheers E5o

---

