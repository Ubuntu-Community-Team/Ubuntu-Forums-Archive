---
title: "Cns"
date: 2014-01-13
forum: Packaging and Compiling Programs
---

### Post by vaidneel on 2014-01-13
[COLOR=#000000]I am trying to compile a program which requires me to execute the command[/COLOR]
[COLOR=#000000][FONT=Courier]source cns_solve_env[/FONT][/COLOR][COLOR=#000000]. However, Ubuntu replies setenv command not found. Please advise.[/COLOR]

[COLOR=#000000]Thanks,[/COLOR]
[COLOR=#000000]Neel[/COLOR]

---

### Post by tomearp on 2014-01-13
That error message occurs because setenv is a C-shell command (csh or tcsh) and Ubuntu uses bash for its shell.
Have a look for a file called cns_solve_env_sh or .cns_solve_env_sh and source that one instead.

---

### Post by oldos2er on 2014-01-13
Moved to Packaging & Compiling Programs.

---

### Post by vaidneel on 2014-01-17
Thanks for the reply. I have changed permanently to csh shell. But this is what I receive.

% make install
/home/rl3m1/Documents/cns_solve_1.3/bin/getarch: Permission denied.
./bin/install: Permission denied.
make: *** [install] Error 1

I am new to ubuntu. Kindly help.

---

### Post by steeldriver on 2014-01-17
Did you run other commands using 'sudo' that may have left the target directory / files owned by 'root'?

---

### Post by vaidneel on 2014-01-20
No, I haven't done that.

---

### Post by steeldriver on 2014-01-20
How did you unpack the archive? I'm guessing /home/rl3m1/Documents/cns_solve_1.3/bin/getarch is a script that probes the machine architecture, and needs to be executable - if it lost its execute (x) permission you may need to use chmod (or the file manager) to make it executable again

---

