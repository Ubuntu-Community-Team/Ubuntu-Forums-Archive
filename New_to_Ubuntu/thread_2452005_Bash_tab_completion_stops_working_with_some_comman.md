---
title: "Bash tab completion stops working with some commands"
date: 2020-10-14
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-10-14
Hello all,

Occasionally tab completion will (seemingly) randomly stop working with certain commands, it will continue to function with others though.

The latest command to stop working was openvpn, I can press tab to complete the actual command but it wont work with any long options or arguments, other commands are working fine with tab completion, and it just stopped working suddenly as I was using it.

I've re-installed openvpn and bash completion, restarted the computer and sourced ~/.bashrc but still it doesn't work. I've had the same problem with other commands in the past which I think probably eventually fixed themselves, but it's rather annoying when it happens, especially for commands which take long, esoteric file paths as arguments.

---

### Post by TheFu on 2020-10-14
If you are going to use a command more than once, put it into a script and store it in your ~/bin/ directory.   Be certain to put enough commenting in each file so you can 'grep' it later when you need a similar solution.

Sorry, I've not experienced what you have.  Could an alias be getting in the way of the completion?  Have to watch out when using aliases or bash functions.

---

### Post by Holger_Gehrke on 2020-10-15
The command line completion is programmable. There are several hundreds of scripts involved if you're counting the specialized scripts in /etc/bash_completion.d/ and /usr/share/bash-completion/completions/ which each encode the syntax and options for a single command. Those scripts are mostly installed by the package bash-completion, but a program can bring along it's own completion script and of course a user could write his own completion-script (although those should go into ~/.local/etc/bash_completion.d/).

If something breaks there are a few tricks for working around the breakage. Meta-! completes a command, Meta-/ completes a path and file name, Meta-@ completes a hostname, Meta-~ completes a username and Meta-$ completes a variable. On most keyboard layouts Meta is bound to the Alt-key.

Holger

---

### Post by jcdenton1995 on 2020-10-18
> **Holger_Gehrke said:**
> If something breaks there are a few tricks  for working around the breakage. Meta-! completes a command, Meta-/  completes a path and file name, Meta-@ completes a hostname, Meta-~  completes a username and Meta-$ completes a variable. On most keyboard  layouts Meta is bound to the Alt-key.

Thanks, this was really helpful.

Just  now worked out that the actual tab completion only works when I sudo  the command, that's why it 'broke', as I was trying to run it without. I  wonder why this could be?

---

