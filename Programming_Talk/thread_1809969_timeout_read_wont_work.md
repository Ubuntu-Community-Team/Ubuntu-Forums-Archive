---
title: "timeout read wont work"
date: 2011-07-22
forum: Programming Talk
---

### Post by KillerLink on 2011-07-22
Hi!

I would like to write a bash script which is waiting for input from the user.
But it should stop waiting for input after a give time.

I found some examples showing the following:
read -t 10 -p "Eingabe erwartet" inputvar;

but it says illegal option: -t

i found this on serveral sites and i wonder why its not working.

so, does somebody have a solution?

Edit: Im using Ubuntu 11.04 and im writing bash scripts.

---

### Post by dwhitney67 on 2011-07-22
> **KillerLink said:**
> 
Edit: Im using Ubuntu 11.04 and im writing bash scripts.

Are you sure that you are using bash?  Ubuntu comes with dash, which is a slimmed down version of bash.

Verify that you have bash installed; an easy way is to examine /bin/bash to ensure that it is not a symlink to /bin/dash.

---

### Post by JupiterV2 on 2011-07-22
Does your script start with #!/bin/sh or #!/bin/bash? I ask because /bin/sh is a symlink to dash on Ubuntu and lacks some of the features bash has. I don't know if this is causing your problem or not.

---

### Post by Bachstelze on 2011-07-22
> **dwhitney67 said:**
> Are you sure that you are using bash?  Ubuntu comes with dash, which is a slimmed down version of bash.

dash is not a "slimmed down version of Bash", it is a completely different and separate shell.

> Verify that you have bash installed; an easy way is to examine /bin/bash to ensure that it is not a symlink to /bin/dash.

Bash is always installed in Ubuntu, alongside with dash, and is the default interactive shell. /bin/sh by default points to /bin/dash but can be made to point to /bin/bash, either manually or through debconf (dpkg-reconfigure dash). It is generally considered a bad idea, though. If a script needs Bash, it should say so and have /bin/bash in the shebang line.

---

### Post by KillerLink on 2011-07-22
hmm okay my script starts with:
#!/bin/sh

im editing an exisitng longer script to my wishes, so i need to stay at this "#!/bin/sh".

questions i have now:
1) im writing dash and not bash, is this correct?
2) how could i get bash, write bash scripts?
3) what do i do in my script whiche has "#!/bin/sh" on top to get a timing out read function?
i need to wait only a given time for input. if time is overlapped it should continue with next programm line.

thanks for already give answers, im counting on further more ; )

---

### Post by Bachstelze on 2011-07-22
1. Probably. Run the command

```
ls -l /bin/sh
```

to know which shell your script runs with.

2. If you want your script to run in Bash, changing #!/bin/sh to #!/bin/bash is the proper way. Alternatively, you can make /bin/sh point to Bash with

```
sudo dpkg-reconfigure dash
```

Answer "No" and /bin/sh will be made to point to /bin/bash. But then your script may not work on systems where /bin/sh does not point to Bash (or which do not have Bash at all).

---

### Post by JupiterV2 on 2011-07-22
> **KillerLink said:**
> hmm okay my script starts with:
#!/bin/sh

im editing an exisitng longer script to my wishes, so i need to stay at this "#!/bin/sh".

I would argue that, since read is an internal command to bash, that NOT requiring your script to use/depend on bash would be a bad idea. /bin/sh could point to tsch, ash, sh, dash, bash, csh, etc. Since read command may not work the same, or at all, on other shells it makes sense to require/depend on bash. I highly recommend changing the shebang to #!/bin/bash. At least then users will know why your script won't run or run as intended.

---

### Post by KillerLink on 2011-07-25
Hey, thank you for all your replies!
I experimented around and found out that i could 
change #!/bin/sh to #!/bin/bash
as you said, and the script still worked, so 
i also was able to use read -t now!

So thank you all, you helped me alot!

---

