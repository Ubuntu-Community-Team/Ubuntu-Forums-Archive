---
title: "Java TextArea Append Problem"
date: 2010-07-08
forum: Programming Talk
---

### Post by telosin on 2010-07-08
So I have this GUI application that runs fairly well apart from one thing. While it's running a process which cycles through a very long method, there are calls to a different method whose only job is to print what's currently happening to the textarea on the GUI. It's not updating to the textarea in real time, though, and instead, it's all printed at the end of the big method. If I replace the log.append("whatever") with System.out.println("whatever"), it does fine in command prompt. Everything works exactly as it should and it prints the second it gets to the S.O.P. in the code. When it's the log.append, though, it waits until the entire method has completely finished and then prints it all to the log at the same time.
I've not done much with GUI programming and I know this could be something with threading but everywhere I've looked, it says that the textarea.append() method is thread safe. I assumed this meant that it doesn't need to be threaded to run but I'm not positive.
Any help would be appreciated and I can post sample code or give more details if needed.
Thanks.

*edit*
Not gonna re-bump this but it was the threading. Thanks everyone, I finally figured it out!

---

### Post by PaulM1985 on 2010-07-08
Have you tried repainting the panel that contains the textarea every time you update it?

(This may slow down your program but the info will be updated more regularly)

Paul

---

### Post by telosin on 2010-07-08
> **PaulM1985 said:**
> Have you tried repainting the panel that contains the textarea every time you update it?

(This may slow down your program but the info will be updated more regularly)

Paul

Just tried that and unfortunately, it didn't work. Thanks for the suggestion though! Any other ideas?
It doesn't matter to me if the solution slows down the program because it's pretty quick as it is.

---

### Post by Reiger on 2010-07-08
Are you running the “big method” on the Event Dispatch Thread? Because that would block all GUI events/updates until your big method has finished. You may want to take a look at SwingWorkers if you hadn't already.

---

### Post by myrtle1908 on 2010-07-08
If you just want a quick fix, have your "big method" run in its own thread, give it a reference to the GUI and have it call an update textarea method.

---

### Post by wkhasintha on 2010-07-09
Culprit must be the Event dispatcher thread. use a separate thread to processor intensive tasks .

---

