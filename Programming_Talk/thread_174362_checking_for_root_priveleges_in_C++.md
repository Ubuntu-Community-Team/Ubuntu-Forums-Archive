---
title: "checking for root priveleges in C++"
date: 2006-05-11
forum: Programming Talk
---

### Post by olsonar on 2006-05-11
Is there an easy way to check to see whether a C++ program is being executed as root?

---

### Post by nagilum on 2006-05-14
You can for example use the getuid (or geteuid) system call to see it the current process is run with uid 0, i.e. root.

---

### Post by olsonar on 2006-05-14
could you be more specific or give an example of it being used? I'm very new to C++. Would it just be something like:

int user;
user = getuid();
if (user == 0)
{
//code to be executed as root
}
else
{
cout << "root privleges needed";
}

---

### Post by wmcbrine on 2006-05-14
Don't write it like that. Check for the specific privileges you actually need, like write access to a certain file; don't check for "root". Then, in most cases, people will be still be able to run the program in limited accounts with those specific privileges.

---

### Post by olsonar on 2006-05-15
the application i'm writing needs to be able to call apt & dpkg both of which must be executed as root. So, would my code work? or is there something I'm missing?

---

### Post by jdong on 2006-05-15
[QUOTE=olsonar]the application i'm writing needs to be able to call apt & dpkg both of which must be executed as root. So, would my code work? or is there something I'm missing?[/QUOTE]

You should attempt to execute apt/dpkg given current permissions, then detect if either tool complains about permissions. It's not 100% safe to assume root/0 is always the superuser ;-)

But in reality, until you have time to write something more elaborate, checking getuid/geteuid will suffice.

BTW, apt and dpkg both have C-accessible API's for their operations; It's always more robust to use those instead of calling the programs externally. Again, if you have the time/effort :)

---

### Post by LordHunter317 on 2006-05-15
> **wmcbrine]Don't write it like that. Check for the specific privileges you actually need, like write access to a certain file said:**
> Under POSIX, the only privilege checks that exist are:[list][*]Filesystem checks that are per user/group[*]Resource limits, that are per-user[*]Everything else privileged requires root[/list]This is a slight simpification, but it's basic enough.  The "standard" UNIX security model doesn't provide for very fine-grained control beyond access to files, and many things are of a binary "root has the privilege, no one else does" manner that you cannot change.  Socket privileges, some I/O operations, many admin privileges (e.g., kernel debugger, shutdown, etc.) are all of this nature.

To be fair, all commerical UNIXes and Linux support models that make this more fine-grained (as does Windows, VMS, pretty much any widespread general-purpose OS but *BSD and OS X).  However, they're not standarized, so you have to do the per-platform work.  For some applications, this may not be worth it.

> Then, in most cases, people will be still be able to run the program in limited accounts with those specific privileges.This should be the goal of any application, but the manner of achieving it on UNIX is privilege or executable seperation, generally.

[quote=olsonar]the application i'm writing needs to be able to call apt & dpkg both of which must be executed as root.No, neither APT nor dpkg have to be called as root all the time.  Both have operations perfectly safe for non-privileged users.  More importantly, unless your application needs privilege for other operations, the right way to do it is probably to invoke them via sudo, unless it's some sort of daemon.

[quote=jdong]It's not 100% safe to assume root/0 is always the superuser[/quote]Actually, it's perfectly safe to assume UID 0 is the superuser.  It's part of the POSIX standard.  It's not safe to assume it's named 'root', however on very old UNIX, breaking that assumption will break some applications. But it's not something normally done anyway, as there is no point.

---

### Post by olsonar on 2006-05-16
so I should just put that code abound the calls that actually require root priveleges? like for installing/uninstalling software?

---

