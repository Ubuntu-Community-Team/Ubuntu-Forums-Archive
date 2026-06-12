---
title: "script to sort a text file"
date: 2013-05-20
forum: Programming Talk
---

### Post by GrouchyGaijin on 2013-05-20
Hi Guys,


I was wondering about having a script sort a text file.
Specifically what I mean is, I have a text file that looks like this:


```

[ ](C)Appointment: TBA
[ ](A)Work task
;Due Date: Mon, May 20, 2013
[ ](B)Language class
;Due Date: Sat, Jun 01, 2013
;;Notes;: 1:00 PM  - Presentation Due
[ ](A)Work task
;Due Date: Mon, May 20, 2013
[ ](E)Appointment
;Due Date: Mon, May 20, 2013
[ ](D)Appointment
;Due Date: Mon, May 20, 2013



```


Is there a way I can have a script sort these from most important (A) to least important (E) 
while keeping the dates and notes with the correct event?


In the end I'd like the text to look like this:


```

[ ](A)Work task
[ ](A)Work task
;Due Date: Mon, May 20, 2013
[ ](B)Language class
;Due Date: Sat, Jun 01, 2013
;;Notes;: 1:00 PM  - Presentation Due
[ ](C)Appointment: TBA
[ ](D)Appointment
;Due Date: Mon, May 20, 2013 
[ ](E)Appointment
;Due Date: Mon, May 20, 2013

```

I tried a couple of things using sort, but wasn't able to keep the due dates and notes with the correct events.

---

### Post by ofnuts on 2013-05-20
Sort alone won't cut it. What you have to do it reformat the file to one line per event (removing the line separators at the right places (when followed by a semicolon, for instance)(possibly using sed), sort that files, and format back the output (likely with sed again).

---

### Post by Vaphell on 2013-05-20
quick and dirty
```
awk '{printf(($0~"^;"?"<EOL>":"\n")"%s",$0)}' in.txt | sort -t'(' -k2 | sed '1d; s/<EOL>/\n/g'
```
```
[ ](A)Work task
;Due Date: Mon, May 20, 2013
[ ](A)Work task
;Due Date: Mon, May 20, 2013
[ ](B)Language class
;Due Date: Sat, Jun 01, 2013
;;Notes;: 1:00 PM  - Presentation Due
[ ](C)Appointment: TBA
[ ](D)Appointment
;Due Date: Mon, May 20, 2013
[ ](E)Appointment
;Due Date: Mon, May 20, 2013
```

---

### Post by GrouchyGaijin on 2013-05-21
Thank you!!
Simply amazing

---

