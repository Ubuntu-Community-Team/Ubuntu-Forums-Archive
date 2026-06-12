---
title: "simple way to gather data from students"
date: 2011-09-19
forum: Programming Talk
---

### Post by surfer on 2011-09-19
i need to do a simple survey with a couple of students. i would like to be able to do this offline (i.e. not having to have a web server running). is there a best practice for something like this?

the method used should also be platform independent.

my first thought was to use pdf (created with LaTeX, LibreOffice or scribus) and extract the data with python afterwards.
evince is able to store the data entered in the pdf, but i'm not sure if the adobe reader on a windows system can do that. and i do not know how this would work on a mac...

then i was thinking about html forms (a local html file with some javascript). the data would be stored in cookies and could be sent as email at the end of the survey.


more ideas? or better ways to the ideas i have described above?

any help is appreciated! thanks in advance.

---

### Post by karlson on 2011-09-19
> **surfer said:**
> i need to do a simple survey with a couple of students. i would like to be able to do this offline (i.e. not having to have a web server running). is there a best practice for something like this?


Most surveys I have seen are done in 3 ways:

1.  Written.  You have a printed copy of a survey that responders fill out and send back.
2.  Online.  Webserver+cookies+something to collect the data into.
3.  Phone.  A human or an automated system gathers responses and processes it into the data analysis server.

---

### Post by surfer on 2011-09-19
thanks for your answer.

the survey has been done in paper up to now. the idea is to automate it i.e. have the students fill out something (electronically) that can be evaluated automatically.

and, as stated before, without a web server.

---

### Post by PaulM1985 on 2011-09-19
You could write a form in HTML.  The participants open the HTML in their web browser, on the click of the submit button, this information could be sent to your email.

I haven't actually done this myself before, but I know it is possible.  Here is a website showing some examples of how it is done:
[http://www.tizag.com/htmlT/forms.php](http://www.tizag.com/htmlT/forms.php)

Paul

---

### Post by surfer on 2011-09-19
yep. this is something along the lines of what i imagined. thanks for the link!

yet other ideas?

---

### Post by juancarlospaco on 2011-09-19
Ehm... the new HTML, can be offline too, like offline gdocs,
its not that hard to do, only make a .manifest file with the list of files needed to work offline

[http://www.html5rocks.com/en/features/offline](http://www.html5rocks.com/en/features/offline)

---

### Post by tubunu on 2011-09-20
I have successfully created electronic True/False and choose correct answer tests with google docs. You need to click on create new form to do that. Then you install a Flubaroo script from the script gallery and it will automatically check all the answers and will even give you percentage, the number of incorrect answers, etc. Highly recommended. I'm not sure it's possible to do that offline though.

---

### Post by surfer on 2011-09-21
two more interesting ideas. thanks!

i will look into both.

> **tubunu said:**
> I'm not sure it's possible to do that offline though.
with the "offline" requirement i just wanted to say that i do not have a webserver available (and dont want one running on my laptop). so this would be a very nice solution.

---

### Post by Tony Flury on 2011-09-22
A free account on Survey monkey will give you simple forms, response deadline, and some simple analysis, though if you want more complex analysis and other features then you have to pay for an account.

---

### Post by nvteighen on 2012-10-29
Let me recommend another online survey service which I've found really useful in the past: SurveyGizmo ([http://http://www.surveygizmo.com/](http://http://www.surveygizmo.com/)). Don't be afraid by the priced plans, there's a student account which is free, but you have to scroll down to the very bottom of the page in order to find it... :P (Here, I'll save you the trip: [http://www.surveygizmo.com/free-student-account/](http://www.surveygizmo.com/free-student-account/))

---

