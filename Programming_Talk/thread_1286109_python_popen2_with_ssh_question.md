---
title: "python popen2 with ssh question"
date: 2009-10-08
forum: Programming Talk
---

### Post by openfly on 2009-10-08
This has to be done with python 2.3 and no extra modules.  As a result popen2 seems the best module to run with.

Please pardon the curses.

```


def ssh_auth(s):
        curses.echo()
        s.erase()
        screen.addstr(4, 2, "SSH Authentication", curses.A_UNDERLINE)
        screen.addstr(6, 4, " Username: ", curses.A_BOLD)
        screen.addstr(8, 4, " Password: ", curses.A_BOLD)
        screen.addstr(6,20, " "*15, curses.A_STANDOUT)
        screen.addstr(8,20, " "*15, curses.A_STANDOUT)
        username = screen.getstr(6,20)
        curses.noecho()
        password = screen.getstr(8,20)
        # screen.addstr(12,20, " %s" % username, curses.A_BOLD)
        # screen.addstr(14,20, " %s" % password, curses.A_BOLD)
        screen.addstr(11,11, " Authentication stored... ", curses.A_BOLD)
        screen.addstr(12,11, " Checking Credentials.... ", curses.A_BOLD)
        try:
                sshauthr, sshauthw, sshauthe = popen2.popen3('/usr/bin/ssh 192.168.1.2 -p 22 -l %s' % username, w+b)
                output = sshauthr.read()
                screen.addstr(12, 36, " %s" % output, curses.A_BOLD)
                sshauthw.write('%s\n' % password)
                output = sshauthr.read()
                screen.addstr(12, 36, " %s" % output, curses.A_BOLD)
                sshauthw.close()
                sshauthr.close()
                sshauthe.close()
        except:
                screen.addstr(12, 36, " Failure! ", curses.A_BOLD)
                traceback.print_exc()

```

So this is failing pretty badly.  It's taking over the stdout of my app without permission and going full interactive on the read() call.  My attempts to pass the password to it with a write() have failed as well seemingly.

What am I doing wrong here?

---

### Post by geirha on 2009-10-08
ssh does not read the password from stdin, it reads it directly from the terminal. Without installing any extra modules, I don't see any other way than to set up public key authentication or host-based authentication to get passwordless login.

---

### Post by openfly on 2009-10-08
Yeah that's impossible.  

How the hell did people use python back before 2.6?  It's such a crap language.  

Any ideas on how to write to tty pre - pexpect ?

---

