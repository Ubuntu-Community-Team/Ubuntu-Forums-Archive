---
title: "HOWTO Check if an app is running and - if not - run it"
date: 2008-12-11
forum: Outdated Tutorials &amp; Tips
---

### Post by skotos on 2008-12-11
Sometimes applications we depend on quit unexpectedly, when we are out and about, far from the keyboard and leave us in desperate conditions: didn't it happen when you were downloading your favourite distro or when you wanted to sftp to your remote server and the service was not running?

Ok, ok.. This is a common cause of stress to all of us. The following code just wants to unobtrusevely show a way - just one - you might follow to limit it and live happily with crashes and your memory black outs.

First of all: **prerequisites!** 
[LIST]
[*]bash
[*]zenity
[/LIST]
 **Bash** was chosen because it is something we cannot live without! (no startup services, logins, essential jobs...)
If our monster were not running a _shell_, Ubuntu itself could not exist: bash is probably the most spreaded shell, but **zshell** is great as well (give that a look when you have enough leasure time).

**Zenity** is a small package that can be easily installed by Synaptics and is probably our best secret!
Zenity, in fact, can provide a very interesting, simple and nice GUI (GUI stands for Graphical User Interface)

Here, we will not cover the most common dialogs but a very undocumented feature: the small applet that can run in our Gnome panel, just near the clock, the trash bin, the volume and the updater applets we generally use.

YES! With just a few lines of Bash scripting and a Zenity command we can provide very useful commands and services: thus the application monitoring is just a sample of what we might accomplish when we will be able to mix them, even if we do not know perl or python, or - simply - we do not want to develop further and more complex features.

Generally speaking, in fact, I look at bash and zenity as a solution for a small to medium script: running from 20 to 200 lines, probably 300 but not more.
Since bash has got its limitations due to its age and scope, a fair bash usage is always recommended. Bash scripts can quickly become very difficult to manage and debug, thus some rules or conventions coming from more recent programming languages can be of help if applied to our scripts: camel case variables, scope and procedures (or functions).
What does this mean? Well, it is always a good habit to use typed variables even if the language allows you to assign a string to what it was an integer just a line above, and it is of great help distinguishing a GLOBAL variable from a local one.
When you change a global, in fact, you can easily disrupt the application, while when you work on a local, every error you have to look at is inside the procedure (or function) that is generally small: 10 to 20 lines of code.
Camel case, instead, helps reading your code weeks, months and years later.

Let's look at a sample: let's write the first lines[php]#!/bin/bash[/php]This is the shabang, the line that tells bash it has to interpret the file a line at a time because it is a sequel of bash commands: internal and external as well. Internal commands cannot be found in the hard disk, the external commands - instead - can be found spreaded all over the system tree: generally inside
[LIST]
[*]/bin
[*]/usr/bin
[/LIST]
but even inside your home directory, by convention inside *~/bin*. I suggest you to create the folowing script inside the latter directory, so that you will be able to work on it with no privileges and security concerns, at least at the beginning.

External commands can be binaries and text files as well: binary files are directly run by the system, text files are scripts that are to be interpreted by an interpreter! Woah! And wtf is an interpreter? Well, it can be a shell like bash, zshell, ksh, csh or a language like perl or python as well!

Let's go deeper in the script!
First of all documentation! We can hide lots of useful information in our script by prepending each line with a hash (#). The hash sign, in fact, tells the shell we are writing something that will not have to be interpreted by it: we might, for instance, store information on licensing, versioning and requirements. Sometimes, comments are even used to help in code readability or to store information other specific applications can interpret to automatically retrieve documentation and generate HTML modules for customers (google a bit for javadoc or preprocessors, an advanced topic).[php]############################
# Author: Me!
# Licence: GPL v3[/php]Now that the basic has been scratched we run in deep and gorgeous details: scope and functions. The scope of a variable can be global or local. For scope we mean the area inside which the variable is defined. Since the variable is just a place where we can put a value that can be constant or changed, a variable can be called variable or constant if it does not change all over the script or program.
A variable that has a particular meaning in a small part of the script is generally defined as local, while one that can be used or changed all over the script is defined (when we cannot encapsulate it in an object, that is an advanced topic) as a global

As a general rule of the thumb: more globals mean less readabilty, less programming skill, great disorder and desperate confusion! Please, remind to avoid GLOBALS as much as possible or you will hurt yourself: you have been warned!![php]## # By convention, every global variable is in UPPER case
# every local variable, instead, will use the camel case and will carry - as prefix -
# the type initial: s for string, n for number, b for bool

##
# Boolean constants (a sort of type emulation)
#
declare -ir TRUE=1
declare -ir FALSE=0

##
# Read only application name (string): it must be in the search path
declare -r MULE=amule

##
# STATUS will hold a string that is to change
declare STATUS

##
# Integers constants (seconds)
declare -ir DURATION=10
declare -ir FREQUENCE=120[/php]The declare and comment statements above just sum up what we have discussed up to now. In particular, the declare statments are followed not only by the variable name, but - often - by a switch that tells us some juicy information: the TRUE, FALSE, DURATION and FREQUENCE globals are integers and read only. This means that the values they have will never change all over the script: so they are CONSTANTS.
Another constant is MULE, but MULE is not an integer: it is a string. Strings are generally enclosed by double quotes, but - in this case, as a rule of thumb - since we assign a word with no spaces, quotes can be omitted.
The following store the same value:[php]declare -r MULE=amule
declare -r mule="amule"[/php]but are not the same: variable names are case sensitive, thus *MULE* and *mule* are two different variables, pointing to different memory locations!
Since you have read all of the above you know that they are GLOBALS and that the preferred naming convention is all UPPER CASE and the MULE is what you will encounter in the script when a global will be referenced, set or checked.

Now let's face functions and local variables[php]##
# @global STATUS
# @return BOOL
function Check() {
    local bRC=${FALSE}
         local sRC="at `date +%H:%M.%S` of `date +%d.%m.%Y` [${MULE}] "

    if [ -z `pidof "${MULE}"` ]; then
        STATUS=$(printf "${sRC}" "IS NOT RUNNING. Thus, the application will be automatically rerun.")
    else
        STATUS=$(printf "${sRC}" "is correctly running.")
        bRC=${TRUE}
    fi

    return ${bRC}
}[/php]Functions are often called procedures or methods. They are small specialized pieces of code. Generally a function returns a value, while a procedure return nothing (or *void*, a special return type). Functions and procedures are called methods by Object Oriented programmers (strange beasts among us who work late at night that you will never want to meet early in the morning, before having a relaxing international breakfast).
The main function syntax is the following:[php]function FunctionName() {
....
}[/php]FunctionName generally uses camel case and the initial is Upper case, but many beasts have different opinions on this (do not mind, for now).
The first two lines inside our function begins with local. Yes, local. Because the variables we are declaring and defining will be useful just inside the function (the variables scope, or area).
Since we are talking of locals, the rule is - as previously anticipated - camel case with prefix: thus bRC stands for bool Return Code and sRC for string Return Code.

We can now proceed and have a look at our conditional statement. The complete form is[php]if [ condtion ]; then
...
else
...
fi[/php]but[php]if [ condtion ]; then
...
fi[/php]can be often enough. Please take note of the spaces between the condition and the square brackets (they might take you mad) and of the semicolon that allows you to have the *then* keyword on the same line of the *if* keyword.
For readability, indenting the content is a must have, but the shell will forgive you if you cannot be polite to yourself and the other programmers who will read your code.[php]if [ -z `pidof "${MULE}"` ]; then[/php]can be translated in plain English as: *if there is no process id belonging to a job named MULE then*.
Woah..WTF! Yes.. There is lots of Unix philosophy here. Let's start frome the inner level: the global MULE is referenced inside "${}" (a good suggested and consistent way to point to the variable). The statement can then be read like this: *if there is no process id beloging to the job _amule_ then*..

Now we can look at the reversed single quotes: these mean that the command pidof amule must be run and that the returned value must replace the expression enclosed by the quotes.
Suppose amule is running and its pid (process id) is 25354: the expression might be read *if 25354 is not null then*

The[php]if [ -z value ]; then[/php]is a contract way to say *if value is not null*

Woah... It was hard, but now, hopefully, clearer... Eh eh eh...[php]       STATUS=...
        bRC=...[/php]are just assignment statements even if $(printf...) may sound a bit strange...at first...
`..` and $() mean just the same: they tell the shell to first run the command inside them!

*printf* is instead a strange beast that C and PHP programmers abuse a bit to reduce space and gain in readability. We can skip it for now. Explaining the printf usage might take a tute by itself: try man printf if you want to scratch the surface of a function you will love more and more the older you get...
Now... Gotta go to sleep but I will not leave you just in the middle of nothing. Here below you find the rest of the source. Part II of this tute will explain in great detail the second and last function and how and why zenity was the choice.[php]##
# @FIXME File descriptor closure
# @return VOID
function Guardian() {
    local x
    local nPauseOnError=5
    
    # Notification applet initialization
    exec 3> >(zenity --notification --listen)
    echo "icon:info" >&3
    echo "message:The ${MULE} guardian has been started" >&3

    while true; do
        Check
        bRC=$?
        if [ ${bRC} -eq ${FALSE} ]; then
            echo "icon:error" >&3
            echo "tooltip:The application status gets checked every ${FREQUENCE} seconds: ${STATUS}" >&3
            ${MULE} &
            sleep ${nPauseOnError}
            let x=${FREQUENCE}-${nPauseOnError}
            echo "icon:info" >&3
            sleep ${x}
        else        
            echo "icon:info" >&3
            echo "tooltip:The application status gets checked every ${FREQUENCE} seconds: ${STATUS" >&3
            sleep ${FREQUENCE}
        fi

    done

    # File descriptor closure. This will also kill zenity, but,
    # currently, there is no way to come here: no docs found on click and/or right click menu availability
    exec 3>&-  
}

# Ok, let's run the main loop
Guardian[/php]This is my first contribute to the community and I hope it can really help you learning how to write bash scripts.

---

