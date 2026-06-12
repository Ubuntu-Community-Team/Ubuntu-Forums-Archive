---
title: "Need your comments on a PyGTK PlayStation CD backup tool"
date: 2007-12-17
forum: Programming Talk
---

### Post by verb3k on 2007-12-17
Hi all,

This is my first post in this section and I hope I get something useful out of it.
I am new to programming and currently learning python, working on a GUI app to backup PSX games using "cdrdao" as a backend.

The program in its current state works just fine, but I can see lots of drawbacks:

1-The program is bloated and the code looks ugly.
2-No object-oriented programming was used. ( I know it's not necessary)
3-Many noobish habits and techniques were used to solve some problems.
4-The use of some shell commands instead of doing things in a pythonic way.

I want you to help me polish it and teach me how to do it the right way (and help me toss those bad techniques away)

I would also appreciate it if someone could tell me why I would want to do it in OOP, what's the benefits? what's object-oriented programming?(still struggling with this question)

Here's the code:
[http://dpaste.com/hold/28221/](http://dpaste.com/hold/28221/)

Note the use of the global variable avail, I am sure there is a better way, but can't come up with it.

Thanks in advance,
verb3k

---

### Post by Quikee on 2007-12-17
insted of:

[PHP]def errors(number):
	if number == 1:
		error_message("Missing Dependency","The program \"cdrdao\" was not found on your system. You can get it from:\nhttp:/cdrdao.sourceforge.net")
	elif number == 2:
		error_message("Error!","An error occurred!")
	elif number == 3:
		error_message("Error!","An error occurred!\n\n1-Did you choose the right CD drive?\n2-Are you sure the game's CD is in the specified drive?\n\nIf none of these solves your problem, contact the author.")
	elif number == 4:
		error_message("Error","The name can only contain letters and/or numbers")
	elif number == 5:
		error_message("Error","You must supply a game name.")
	elif number == 6:
		error_message("Error","The supplied directory does not exist.")
	elif number == 7:
		error_message("Error","You don't have \"write\" perrmissions to the specified directory.")
	elif number == 8:
		error_message("Error","You don't have \"execute\" perrmissions to the specified directory.")
	elif number == 9:
		error_message("Error","Files with the same name already exist.")[/PHP]



[PHP]
error_messages = (
	("Missing Dependency","The program \"cdrdao\" was not found on your system. You can get it from:\nhttp:/cdrdao.sourceforge.net"),
	("Error!","An error occurred!"),
	("Error!","An error occurred!\n\n1-Did you choose the right CD drive?\n2-Are you sure the game's CD is in the specified drive?\n\nIf none of these solves your problem, contact the author."),
	("Error","The name can only contain letters and/or numbers"),
	("Error","You must supply a game name."),
	("Error","The supplied directory does not exist."),
	("Error","You don't have \"write\" perrmissions to the specified directory."),
	("Error","You don't have \"execute\" perrmissions to the specified directory."),
	("Error","Files with the same name already exist."),
)

def errors(number):
	title, text = error_messages[number]
	error_message(title, text)[/PHP]

Rename error_message to show_error_message or something more appropriate.

Also:

[PHP]def message(title,text):
	dialog=gtk.MessageDialog(
			parent			= window,
			flags			= gtk.DIALOG_DESTROY_WITH_PARENT | gtk.DIALOG_MODAL,
			type			= gtk.MESSAGE_INFO,
			buttons			= gtk.BUTTONS_CLOSE,
			message_format	= text)
	dialog.set_title(title)
	dialog.run()
	dialog.destroy()


def error_message(title,text):
	dialog=gtk.MessageDialog(
			parent			= window,
			flags			= gtk.DIALOG_DESTROY_WITH_PARENT | gtk.DIALOG_MODAL,
			type			= gtk.MESSAGE_ERROR,
			buttons			= gtk.BUTTONS_CLOSE,
			message_format	= text)
	dialog.set_title(title)
	dialog.run()
	dialog.destroy()[/PHP]

Code duplication is considered bad. You could do something like this:

[PHP]severity_level_for_message_box = {
	'INFO' : gtk.MESSAGE_INFO,
	'ERROR' : gtk.MESSAGE_ERROR
}

def message_box(title, text, severity):
	dialog=gtk.MessageDialog(
			parent = window,
			flags = gtk.DIALOG_DESTROY_WITH_PARENT | gtk.DIALOG_MODAL,
			type = severity_level_for_message_box[severity],
			buttons = gtk.BUTTONS_CLOSE,
			message_format	= text)
	dialog.set_title(title)
	dialog.run()
	dialog.destroy()

def errors(number):
    title, text = error_messages[number]
    message_box(title, text, 'ERROR')  [/PHP]

---

### Post by slavik on 2007-12-17
may I suggest looking into libglade?

---

### Post by Wybiral on 2007-12-17
> **slavik said:**
> may I suggest looking into libglade?

I second that. It will make it easier to maintain later. Dynamic widget creation should be reserved for applications that require their interface to dynamically alter itself, this one is stationary so I would just use Glade.

My other critique (since you asked) is to use 4-space tabs instead of regular tabs (it's practically [standard]("http://www.python.org/dev/peps/pep-0008/") in Python, and is definitely considered good practice).

---

### Post by verb3k on 2007-12-17
Thanks Quikee for those corrections .... will be studied indeed :)

slavik and Wybiral, I agree ...I should have used glade but I thought as I was learning, I needed to know how to do a GUI myself rather than using a builder. I think I am starting to understand some basics.
I also like the idea that my program is only one file :)

---

### Post by slavik on 2007-12-17
understandable, but the counterpoint to the one file program is that (while not in this case) sometimes splitting your program into separate files is very good for maintainability (library/front end is a very common split).

---

### Post by verb3k on 2007-12-17
> **Quikee said:**
> 

[PHP]
error_messages = (
	("Missing Dependency","The program \"cdrdao\" was not found on your system. You can get it from:\nhttp:/cdrdao.sourceforge.net"),
	("Error!","An error occurred!"),
	("Error!","An error occurred!\n\n1-Did you choose the right CD drive?\n2-Are you sure the game's CD is in the specified drive?\n\nIf none of these solves your problem, contact the author."),
	("Error","The name can only contain letters and/or numbers"),
	("Error","You must supply a game name."),
	("Error","The supplied directory does not exist."),
	("Error","You don't have \"write\" perrmissions to the specified directory."),
	("Error","You don't have \"execute\" perrmissions to the specified directory."),
	("Error","Files with the same name already exist."),
)

def errors(number):
	title, text = error_messages[number]
	error_message(title, text)[/PHP]



I think this way is slower the the previous, because the interpreter will have to slice the error  messages and assign them and their titles to 2 variables and then operate on them every time messages are needed to be displayed, surely not that big difference but I like faster programs.

Don't you think that's true?

---

### Post by Quikee on 2007-12-18
> **verb3k said:**
> I think this way is slower the the previous, because the interpreter will have to slice the error  messages and assign them and their titles to 2 variables and then operate on them every time messages are needed to be displayed, surely not that big difference but I like faster programs.

Don't you think that's true?

I really don't know - it should be faster because you don't go through all ifs and compare if the number is the input number. And I also used tuples instead of lists which are "faster" (they are immutable which means they can't change once they are created - like strings) than regular lists. So this would be generally identical to:
[PHP]
error_messages = [
    ["Missing Dependency","The program \"cdrdao\" was not found on your system. You can get it from:\nhttp:/cdrdao.sourceforge.net"],
    ["Error!","An error occurred!"],
    ["Error!","An error occurred!\n\n1-Did you choose the right CD drive?\n2-Are you sure the game's CD is in the specified drive?\n\nIf none of these solves your problem, contact the author."],
    ["Error","The name can only contain letters and/or numbers"],
    ["Error","You must supply a game name."],
    ["Error","The supplied directory does not exist."],
    ["Error","You don't have \"write\" perrmissions to the specified directory."],
    ["Error","You don't have \"execute\" perrmissions to the specified directory."],
    ["Error","Files with the same name already exist."],
]

def errors(number):
    error = error_messages[number]
    title = error[0]
    text = error[1]
    error_message(title, text)  
[/PHP]

Anyway you should not notice any difference.. also first priority should not be optimisation but that it works correctly and doesn't crash. Optimisations can then be applied later.

---

### Post by verb3k on 2007-12-18
Thanks Quikee for your support :)

Any other comments are welcome.

---

