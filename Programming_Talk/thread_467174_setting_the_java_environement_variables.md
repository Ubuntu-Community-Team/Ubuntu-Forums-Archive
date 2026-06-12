---
title: "setting the java environement variables"
date: 2007-06-07
forum: Programming Talk
---

### Post by ramory on 2007-06-07
Hi all,

Trying to work with java in my recently installed feisty ,I downloaded Jdk via adept, but I didn't succeed to correctly set the environement variables this is what I did :
```
export JAVA_HOME=/usr/lib/jvm/java-1.6.0-sun-1.6.0.00
```
and then 
```
$ export PATH=$PATH:$JAVA_HOME/bin
```
but when I open a new terminal and do 
```
$ echo $JAVA_HOME
```
i get nothing... I really don't understand what I did wrong!!

---

### Post by meatpan on 2007-06-07
The reason you cannot see JAVA_HOME is because you opened a new terminal.   When a new terminal is opened, the session environmental variables are set to their defaults.  JAVA_HOME will still be defined in the terminal where it was originally input, but not a new terminal. 

You can change the default user environment variables by editing the ~/.bashrc file.  The bashrc file is read every time you open a terminal or when you log in to the machine.  (note, .bash_profile is also read when you first log in). 

A java setup can require a *lot* of environment tweaking, so here are two commands that you might find useful for inspecting your environment:

1. env.  This command will simply print out the environmental variables that would be available to a command you execute.  
2. set.   Straight from the set manual, "Without  options, the name and value of each shell variable are displayed.

I

---

### Post by ramory on 2007-06-07
Hi,

these must sound stupid but what exactly do I need to edit in the ~/.bashrc file??
I didn't find where I can specify the JAVA_HOME and add it directory to the PATH!

thank you..

---

### Post by meatpan on 2007-06-07
The commands you typed in the shell should be adequate for the ~/.bashrc file.  Here is what you wrote:
```

export JAVA_HOME=/usr/lib/jvm/java-1.6.0-sun-1.6.0.00
export PATH=$PATH:$JAVA_HOME/bin

```

Try copying that snippet into the ~/.bashrc.   Open a new terminal, try the env command (for example:  "env | grep -i java"), and see if it worked.

edited: code tags

---

### Post by ramory on 2007-06-07
THANX a lot !!!
it worked just fine thank you...

---

### Post by kawk on 2007-06-07
hello

I would like to ask how do I let eclipse know about the java_home since it uses the default java installed with ubuntu???

---

### Post by nitro_n2o on 2007-06-08
For configuring eclipse: 
Go to: window -> preferences -> Java (on the left side) -> Installed JREs 
Then click on Add.. browse for your java_home and select it 

Hope that helps

---

### Post by ekanata on 2007-06-14
I use these instruction to tell which java to use:
```

update-java-alternatives -l
sudo update-java-alternatives -s <your_chioce>
```
If I already know which java to use, then I don't need the first instruction to show the available versions.
That's what I learn from [here]("http://www.schabell.com/2006/11/ubuntu-java-moving-from-14-to-15-using.html").

---

### Post by nicktmro on 2007-07-12
Putting the JAVA_HOME in your .bashrc won't help if you need to create a launcher for Eclipse for example.

The .bashrc variable will only be available when you use a terminal. 

I think the best place to put your JAVA_HOME is the /etc/environment file as this will be picked up from X as well.

Have a look at [http://tmro.blogspot.com/2007/07/ubuntu-and-java-javahome-no-longer.html](http://tmro.blogspot.com/2007/07/ubuntu-and-java-javahome-no-longer.html)

HTH

---

