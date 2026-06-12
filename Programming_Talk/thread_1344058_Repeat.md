---
title: "Repeat?"
date: 2009-12-02
forum: Programming Talk
---

### Post by Chamillionaire2 on 2009-12-02
What's Up?

OK, So I've been making a script in terminal and have finally ran into a wall, Basically at the end of the script i want it to go right back to the top and start again. Like the MS DOS goto command.

Anyone know?

Thanks Bye.

---

### Post by ajgreeny on 2009-12-02
** 2  Shorthand at the Command Prompt**

   Some of these are specific to the bash shell. I have not experimented enough with other shells to know which are common to all shells. See also the ``Bash Reference Card'', SSC (2000), available online.  
  

[LIST]
[*] / - root directory    
[*] ./ - current directory    
[*] ./command_name - run a command in the current directory when the current directory is not on the path    
[*] ../ - parent directory    
[*] ~ - home directory    
[*] $ - typical prompt when logged in as ordinary user    
[*] # - typical prompt when logged in as root or superuser    
[*]** ! - repeat specified command  **  
[*]** !! - repeat previous command  **  
[*] **^^ - repeat previous command with substitution  **  
[*] & - run a program in background mode
[/LIST]

---

### Post by endBc on 2009-12-02
```
while [ 1 ]
do
    # Instructions
done
```

Alternatively you could use a function which depending on the outcome would call itself again and again until you tell it to stop.

---

