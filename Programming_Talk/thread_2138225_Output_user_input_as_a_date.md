---
title: "Output user input as a date"
date: 2013-04-23
forum: Programming Talk
---

### Post by GrouchyGaijin on 2013-04-23
Hi I'm back with more questions.

How can I take user input and display that as a date?

For example, I can use:
```
read -p "Enter the DATE: " When
```
This will give $When the value of whatever the user types, right?

My question is if the user types in the word Today, how can I have the script assign Today the meaning of the current date and place today's date in the $When variable.

In the end this script writes the variables $When $Name and $Duration to a text file that logs hours spent on different jobs.

---

### Post by steeldriver on 2013-04-23
You could maybe use the system 'date' function

```
$ date --date="Today"
Tue Apr 23 10:47:11 EDT 2013

```

```

$ when="Today"; when=$(date --date="$when"); echo "$when"
Tue Apr 23 10:48:36 EDT 2013

```

It's pretty good at understanding what you mean but you will nevertheless need to add some way to handle invalid input

```
$ date --date="Next Thursday"
Thu Apr 25 00:00:00 EDT 2013

$ date --date="groundhog day"
date: invalid date `groundhog day'

```

---

### Post by GrouchyGaijin on 2013-04-23
Hey thanks man - I'll give that a try!

---

