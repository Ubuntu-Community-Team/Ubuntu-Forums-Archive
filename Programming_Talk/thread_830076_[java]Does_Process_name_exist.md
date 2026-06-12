---
title: "[java]Does Process name exist?"
date: 2008-06-15
forum: Programming Talk
---

### Post by Pyro.699 on 2008-06-15
Hello,

I have created a script that will type into the terminal "wget -l filename ..." a few time and what im looking to do is figure out how i can tell if the process is finished running. I was thinking that you could check the process list to see if "wget" is present. Wget is not executed from the script its self so you cannot get a process id from it. If possible i would like the script not to run tasks that could raise system memory usaged because it takes anywheres from 3-4 hours for all the wget scripts to finish.

Thank you very much for any assistances
~Cody Woolaver

---

### Post by xlinuks on 2008-06-15
> **Pyro.699 said:**
> Hello,

I have created a script that will type into the terminal "wget -l filename ..." a few time and what im looking to do is figure out how i can tell if the process is finished running. I was thinking that you could check the process list to see if "wget" is present. Wget is not executed from the script its self so you cannot get a process id from it. If possible i would like the script not to run tasks that could raise system memory usaged because it takes anywheres from 3-4 hours for all the wget scripts to finish.

Thank you very much for any assistances
~Cody Woolaver
What does the script have to do with Java?

---

### Post by Pyro.699 on 2008-06-15
Using java i need to get the process list to make the next step in the code. What happens is the script open up several "wget" terminals and begins. I need a simple way to make sure that all the wget processes have ended. Opening all these terminals is located in the middle of the script.

Thanks again
~Cody Woolaver

---

### Post by xlinuks on 2008-06-15
Java doesn't have any API function to get the list of processes of a given OS. You'll have to manually code it. I guess you'll want to use on the java side the Runtime and Process classes, and the "ps aux" command on the linux side - run through the above two classes of course, then do manual parsing, but again, I don't think it's java you wanna use for that purpose.
Java is a general purpose language when it comes to desktop applications.

---

