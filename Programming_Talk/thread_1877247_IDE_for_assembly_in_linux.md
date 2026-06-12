---
title: "IDE for assembly in linux"
date: 2011-11-07
forum: Programming Talk
---

### Post by ltwinner on 2011-11-07
I am sick of having to use gdb through the terminal and constantly mixing up 'x' and 'print' and their parameters for examining variables and having to manually type in break points. 

Visual Studio has an assembly debug window, a registers window and memory windows which makes it much easier to focus on what is happening in the program.

Is there anything similar available for linux?

---

### Post by ofnuts on 2011-11-07
> **ltwinner said:**
> I am sick of having to use gdb through the terminal and constantly mixing up 'x' and 'print' and their parameters for examining variables and having to manually type in break points. 

Visual Studio has an assembly debug window, a registers window and memory windows which makes it much easier to focus on what is happening in the program.

Is there anything similar available for linux?DDD is a graphical front-end to GDB.

---

### Post by pbrane on 2011-11-08
Nemiver is another graphical debugger available in the repos. It's more in line with a visual studio type of debugger.

---

### Post by ltwinner on 2011-11-09
> **pbrane said:**
> Nemiver is another graphical debugger available in the repos. It's more in line with a visual studio type of debugger.

Ok, Ive download nemiver as I think it is exactly what Im looking for, but I cant get it to work.

I open it and click File->Load Executable and then in the dialog I choose my simple assembly program and click Excute. All that happens then is a new dialog appears that says 'Program exited'. Nothing appears in the main nemiver window or the console below it.

I then tried Attach to Running Program, and selected the gnome-screensaver process and again nothing happened.

I think I tried nemiver last year when I was doing some assembly work and I had the same problem.

So does anyone know how I can get it working as it is really slowing me down having to compile, link and debug programs through the terminal?

---

### Post by pbrane on 2011-11-09
set a break point after you load the program, before you execute. I haven't used nemiver with assembly before, but the it should work. I assume you have the assembler source? Normally nemiver will break on the main() function. You must not have a main in your program.

---

### Post by |{urse on 2011-11-09
Well, I was hoping to just hand you a link but I cant seem to google one up.

If you can find a download link for it "hyde hla linux" IDE is awesome and has win/nix versions.

---

### Post by |{urse on 2011-11-09
Once you find and install HLA, this will help also.

[http://www.masm32.com/board/index.php?PHPSESSID=91437b306c961e724e6ec44d527bc6db&topic=7955.0](http://www.masm32.com/board/index.php?PHPSESSID=91437b306c961e724e6ec44d527bc6db&topic=7955.0)

---

### Post by ltwinner on 2011-11-13
> **pbrane said:**
> set a break point after you load the program, before you execute. I haven't used nemiver with assembly before, but the it should work. I assume you have the assembler source? Normally nemiver will break on the main() function. You must not have a main in your program.

I cant set any breakpoints because there is no code to set them on. The main window is blank. Whether I select Load Core File or Load Executable it is blank.

I am running ubuntu through virtual box if that makes any difference, but I can see it how it would as every single other thing in ubuntu works fine.

I am going mad having to use the terminal all the time when working with assembly.

---

