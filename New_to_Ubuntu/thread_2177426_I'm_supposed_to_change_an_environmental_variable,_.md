---
title: "I'm supposed to change an environmental variable, what does that mean"
date: 2013-09-28
forum: New to Ubuntu
---

### Post by adam20 on 2013-09-28
The instructions for the program I'm trying to run is Set the BT2_HOME environment variable to point to the new Bowtie 2 directory containing the bowtie2, bowtie2-build and bowtie2-inspect binaries. This is important, as the BT2_HOME variable is used in the commands below to refer to


What do I need to do?

---

### Post by GrouchyGaijin on 2013-09-28
Did you look at this page? [https://science.nichd.nih.gov/confluence/display/znt/Bowtie+2+Aligner](https://science.nichd.nih.gov/confluence/display/znt/Bowtie+2+Aligner)

---

### Post by drmrgd on 2013-09-28
Environmental variables are global variables to the shell you're working in and accessible anywhere when you're working in that shell.  The idea here is that 'BT2_HOME' will be an environmental variable that needs to know the directory where you have installed those binaries (i.e. executable programs for BowTie).  So, for instance, if you installed bowtie to '/home/adam20/bowtie/', BT2_HOME should be set to that path:

```

BT2_HOME="/home/adam20/bowtie/"

```

Now if you check the value of BT2_HOME by running:

```

echo $BT2_HOME

```

you will see that the variable is now set to that value.  However, this is for the current session only, and if you start a new session (e.g. open a new terminal window), it will not be set.  So, you'll want to add this command to your .bashrc file, which is loaded each time you start a new login shell.  A simple way to do that is:

```

cp ~/.bashrc ~/.bashrc.bak && echo "export BT2_HOME="/home/adam20/bowtie/"" >> ~/.bashrc

```

Again note, that you'll have to change that path to the actual location of the BowTie binaries!  The command above will make a backup copy of .bashrc (just in case!), and then add the assignment of the bowtie2 path to the BT2_HOME variable in your .bashrc.  Now whenever you start a new shell, this variable will be set for you.  For the current shell you're working in, you'll have to re-load that .bashrc file, which is easily done by:

```

source ~/.bashrc

```

You'll also likely want to add the location of these BowTie binaries to your PATH environment variable in order to be able to call the binary without having to specify the entire path each time.  This can be accomplished in a similar way as above, by adding a line like this to your .bashrc:

```

echo "PATH=$PATH:$BT2_HOME" >> ~/.bashrc

```

That will now add the newly created BT2_HOME variable (which contains the path to the binaries) to your PATH variable so the shell knows where to locate those binaries and you don't need the full path each time.  Don't forget to re-load your .bashrc file to make the changes take effect for the current shell session.  Now you can type something like:

```

which bowtie2-align

```

and you should see the correct path.  

Hope that helps you get started.

---

### Post by Impavidus on 2013-09-28
The instruction suggest, but don't clearly state, that the path to those executables should be added to the PATH variable. They just talk about the BT2_HOME environment variable. So add```
export BT2_HOME="/path/to/directory/"
``` to your .bashrc file. If you wish you can also add the path to your PATH (as explained by drmrgd). This may be convenient, but not really necessary for the program you want to run.

The "export" is important. Without the "export" it just creates a shell variable. "export" turns it into an environment variable, which is inherited by child processes.

---

### Post by adam20 on 2013-09-29
This helped, thanks.  I realized that they were just asking for the path I created and not and actually path

---

