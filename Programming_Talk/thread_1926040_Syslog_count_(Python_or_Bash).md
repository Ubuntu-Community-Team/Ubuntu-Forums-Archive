---
title: "Syslog count (Python or Bash)"
date: 2012-02-15
forum: Programming Talk
---

### Post by pafoo on 2012-02-15
Hello, I am trying to find a way to get a count on how many syslog  messages per second/hour my syslog server is getting. How could I  accomplish this?

---

### Post by pafoo on 2012-02-16
Nobody has an idea?

---

### Post by r-senior on 2012-02-16
I'd probably extract the relevant part of the date/time from each line in the syslog and make a dictionary keyed by that string. As each line is read, increment the corresponding value in the dictionary. Then iterate over the dictionary to get your results, printing based on threshold or sorted in some way.

That would mean I'd use Python rather than Bash.

---

### Post by Zugzwang on 2012-02-16
[LIST=1]
[*]Find out how your syslog server is saving the messages, and in which format
[*]Determine what "messages/second" or "messages/hour" means for you. Over what interval do you want to compute this value? Since messages are an instantaneous thing, but time is not, you will need to specify something like an interval for this.
[*]Write a script to read the messages from their storage and count according to your criterion.
[/LIST]

---

### Post by pafoo on 2012-02-16
Awesome idea, ill start working on it.

---

