---
title: "What language to use for a new programmer with a specific project in mind?"
date: 2006-11-27
forum: Programming Talk
---

### Post by starchildmom on 2006-11-27
Other than some very basic Basic and normal website development stuff (html, edit but not write php files, javascript, etc.), I have no programming experience. I am not looking to become an expert programmer. I have a specific project that I want to do in the most suited language.

The project is a homeschool planner similar to windows programs like [http://www.contechsolutions.net/products/eths_pc/index.htm](http://www.contechsolutions.net/products/eths_pc/index.htm) and [http://www.homeschooltracker.com/](http://www.homeschooltracker.com/) , but that will run on linux and be FOSS . It would be a plus if it could also run on Windows. 

From reading the forums I get the idea that Python is a good place for a beginner to start. Will that work for this project? I realize I am being ambitious for a beginner, but it is something I really want to do. any advice is appreciated.

---

### Post by Choad on 2006-11-27
python would indeed be perfectly suitable for this

you got py-sql for interfacing with a database, and py-gtk/py-glade for the GUI aspects

i only *very* briefly looked at the things u wanted to make... and the sites are not giving me much info lol. at least none that i can be bothered to find

if you would describe the features of this program i think people could help you more 

i am rather keen on c# these days because im being taught it, so i would probably try it in that, but python is good too. im sure you'll be recomended a half dozen languages now lol

---

### Post by coder_ on 2006-11-27
I'd suggest Python for a simpler task like this.  You can also check out Ruby or C# (using Mono) for this, which all have simple Gtk bindings and GUI editors.  C# uses Stetic, built into Monodevelop, and Ruby and Python can use Glade I believe.  Also, you said you want it to run on Windows, Gtk is windows compatible, but slow on Windows.  I'd suggest WxWidgets with Python for crossplatform GUI development.  Also, I believe Tkinter is crossplatform, but WxWidgets seems like the better choice. :)

---

### Post by starchildmom on 2006-11-27
I think I am understanding:) 

Some of the features would be:

Lesson planning by task

Exporting those tasks to a calender based schedule (example: History is assigned on Mondays and Wed., choose the week's history lessons from the lesson plan and have them automatically entered in the correct place in the schedule)

Chore and extracurricular activities integrated like the above.

Report printing of various types of information.

Grade keeping...both traditional (weighted an non-weighted) and a looser more journal like format for families that do not do grades.

Goal listing and tracking

Transcript generation

A way to print out pages so they look nice, maybe with clip art choices, etc.

Reward generator.

Scope & Sequence tracking.

Curriculum Planner.

Separate student and teacher log-ins where the kids do not have access to teacher only features.

Clickable links in everything so that files like ebooks, pdfs and programs assigned to a lesson can automatically be opened. 

Some sort of standardized format so families could share lesson plans and have them easily imported.

Multiple student tracking.

Integration of multiple student schedules at different levels (all activities, just chore, just extracurricular).

Being able to generate the reports in formats where they could be posted on a webpage and at least viewed on a pda would be nice.

Probably the most difficult, but often requested by homeschoolers, is a compatible Palm OS version that can be synced.

As a gratuitous feature, I want it to be pretty :) The windows based programs I have used have been hard on the eyes.

I am going to spend some time on the python lesson recommended in another thread this afternoon.

Thanks for the suggestions!

---

### Post by Ramses de Norre on 2006-11-27
Java would do the job very good to, you can use the swing library for cross platform gui design.

---

