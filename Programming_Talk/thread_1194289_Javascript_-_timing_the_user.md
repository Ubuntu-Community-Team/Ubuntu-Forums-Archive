---
title: "Javascript - timing the user"
date: 2009-06-22
forum: Programming Talk
---

### Post by jit.sd on 2009-06-22
Hey , 
I have a page which does some work that takes about 1-5 seconds , depending on the input . The work is done by javascript , basically calculating distances from the user source to possible destinations and then sorting them . Anywhoo the work is not imp , what i want to do is have a timer that times the amount of time it takes to complete the work . That is when the "startWork()" function is executed the timer should start and when the work is done the "workComplete()" function will be executed and the timer should stop and display how much time was taken . 

How do i do this with javascript ? Any ideas , could u maybe guide me to a page which shows how to .

thanks jit .

heres a link to my page : [http://www.thrice.be/search_page.php]("http://www.thrice.be/search_page.php")

---

### Post by Mirge on 2009-06-22
Firebug with it's timing capabilities imo...

[http://stackoverflow.com/questions/53802/what-is-the-best-tool-to-benchmark-my-javascript](http://stackoverflow.com/questions/53802/what-is-the-best-tool-to-benchmark-my-javascript)

---

### Post by Can+~ on 2009-06-22
x = [getTime()]("http://www.quackit.com/javascript/javascript_date_and_time_functions.cfm") when startWork() is called, then y = getTime() when completeWork is executed.

Total time y - x seconds.

Or you meant a timer that actually updates on real time? I would suggest skipping that an use a .gif animation to at least give the sense that's actually "working".

---

