---
title: "[Eclipse + CDT]. Unable to &quot;Run&quot; a program."
date: 2005-11-19
forum: Programming Talk
---

### Post by ricardo06 on 2005-11-19
I installed Eclipse 3.1.1 +  CDT. 
And it looked ok.

As I don't know this IDE I went thru the tutorial to build my first "hello Ricardo" program. All went well. But It is not possible to run the sample with the "Run" command from the "Run" menu. I followed the instructions and made the relevant choice in the Run dialog. But it would not Run (release or debug) :( .

What is strange is that the executable is produced and runs normaly outside of the IDE :KS . 
Also in the project view the "hello world" binary is qualified "nonele", I think this should display something like x86 or x86_64 :confused: 
Also the Run configuration dialog box complains about the debugger not being supported by the architecture, but GDB is there and runs perfectly.

Thanks to anybody that can help.

Richard


I run Breezy on amd64 3500+.

---

### Post by cstudent on 2005-11-19
If you are talking about running the program in the console view of Eclipse, I have had problems with it display a program correctly. Yet the program was written correctly and ran fine using the terminal. Although I never researched it, I think it's a bug in Eclipse. I just started running the programs outside the Eclipse environment.

Bill

---

### Post by Single on 2005-11-19
After building the project, go to Run menu > Run...
On the left side **double click** on the "C/C++ Local Application", select the generated "configuration". Select the Main tab on the right side and click "Search Project". Select the binary u wan to run from the list and click OK. 
Select the Debugger tab and make sure "GDB Debugger" is selected in the drop down list bellow.
After that click Apply then click Run.

This is actually explained in the official tutorial...

---

### Post by cstudent on 2005-11-19
I have those settings already in place. Sometimes programs will act funky in the console view.

---

### Post by ricardo06 on 2005-11-19
[QUOTE=Single]After building the project, go to Run menu > Run...
On the left side **double click** on the "C/C++ Local Application", select the generated "configuration". Select the Main tab on the right side and click "Search Project". Select the binary u wan to run from the list and click OK. 
Select the Debugger tab and make sure "GDB Debugger" is selected in the drop down list bellow.
After that click Apply then click Run.

This is actually explained in the official tutorial...[/QUOTE]

That is exactly what i did. Now I noticed that  clicking "Run" in the dialog box does not do anything, instead I clicked 'Run' from the tool bar and it did ran in the console view. 
Thankyou to all.

Richard

---

### Post by panchtatvam on 2012-11-09
In my case too I'm just able to compile the Hello world program but unable to run it. While trying to run the binary file (in either debug or release mode) I'm prompted with **" The selection cannot be launched, and there are no recent launches"** .

Eclipse build is Juno.

Also the binary file gets appended with "x86_64/le" every time the code is build for the first time. Is this an issue of x86 vs 64 build ? or is it some compiler issue ?
:(

---

