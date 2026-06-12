---
title: "Python - My first GUI App, feedback please"
date: 2010-05-10
forum: Programming Talk
---

### Post by Bodsda on 2010-05-10
Hi Guys,

I have finally stopped swearing at GTK long enough to create my first ever graphical app. It is a very basic password strength checker. Any and all feedback would be greatly appreciated. I know it is nothing special, but I feel quite proud of it :)

```

#! /usr/bin/env python

import gtk
import string

class Password:
    def __init__(self):
        window = gtk.Window()
        window.set_default_size(350, 250)
        vbox = gtk.VBox(False, 10)

        self.entry = gtk.Entry()
        self.entry.set_text("Please enter your password for strength testing.")
        self.entry.set_editable(True)

        button = gtk.Button("Test Password Strength")
        button.connect("clicked", self.strength)

        self.label = gtk.Label(" ")
        self.label.set_visible(False)

        vbox.pack_start(self.entry, False, False, 10)
        vbox.pack_start(button, False, 20)
        vbox.pack_start(self.label, False, 10)

        window.connect("destroy", lambda w: gtk.main_quit())
        window.add(vbox)
        window.show_all()

    def strength(self, widget):
        password = self.entry.get_text()
        points = 0
        has_punctuation = 0
        has_number = 0
        has_capital = 0
        has_lower = 0
        has_space = 0

        for i in password:
            if i in string.punctuation:
                has_punctuation = 1

            if i in string.digits:
                has_number = 1

            if i in string.ascii_uppercase:
                has_capital = 1

            if i in string.ascii_lowercase:
                has_lower = 1

            if i == " ":
                has_space = 1

        total = has_punctuation + has_number + has_capital + has_lower + has_space

        if total == 1:
            strength = "Very Weak"

        elif total == 2:
            strength = "Weak"

        elif total == 3:
            strength = "Moderate"

        elif total == 4:
            strength = "Strong"

        elif total == 5:
            strength = "Very Strong"

        print strength

        self.label.set_text("Your password strength is: %s" % strength)
        self.label.set_visible(True)




Password()
gtk.main()

```

Thanks!
Bodsda

---

### Post by v1ad on 2010-05-10
looks good, i am glad to see your progressing.

---

### Post by Bodsda on 2010-05-10
Hmm, my dad is getting an error when he runs this

saying that gtk.Label has no attribute set_visible - the only thing I can see is that he has python-gtk2 v2.16, I have 2.17 - do you think this is the issue?

Bodsda

---

### Post by StephenF on 2010-05-10
The strength function contains lots of repetition which can conceal bugs in as yet untested code branches.

In contrast:
```

import string

password = frozenset("Hello World!")

tests = tuple(frozenset(x) for x in (
            string.punctuation, string.digits, string.ascii_uppercase,
            string.ascii_lowercase, string.whitespace))

rankings = ("Nobody expects a blank password", "Very Weak", "Moderate",
            "Strong", "Very Strong", "Authorized personnel only")
        
score = sum(1 for test in tests if password.intersection(test))

print "Password strength is:", rankings[score]

```

---

### Post by Viva on 2010-05-10
Passwords generally don't have spaces, so you should warn the user if he uses a space.

---

### Post by jeffathehutt on 2010-05-10
Instead of using set_visible(), you can use show() and hide() on the label to have the same result.  That should take care of the error.

Also, your program looks nice, keep up the good work! :)

---

### Post by steeleyuk on 2010-05-11
> **Bodsda said:**
> Hmm, my dad is getting an error when he runs this

saying that gtk.Label has no attribute set_visible - the only thing I can see is that he has python-gtk2 v2.16, I have 2.17 - do you think this is the issue?

Bodsda

2.16 doesn't have the .set_visible method, though I don't think you need it anyway.

---

### Post by Bodsda on 2010-05-11
> **jeffathehutt said:**
> Instead of using set_visible(), you can use show() and hide() on the label to have the same result. That should take care of the error.
 
Also, your program looks nice, keep up the good work! :)
 
That works, cheers :)
 
Bodsda

---

### Post by Bodsda on 2010-05-12
Hey Guys,

Just wanted to keep you updated about my progress. The code below is v0.1 of my little password checker. This version includes a new layout and the ability to generate a new Strong or Very Strong password at the click of a button :)

```

			#! /usr/bin/env python

import gtk
import string
import random

class Password:
	def __init__(self):
		
		window = gtk.Window()
		hbox = gtk.HBox(True, 10)
		table = gtk.Table(5, 2, True)
		button1 = gtk.Button("Test Strength")
		button2 = gtk.Button("Generate Password")
		label1 = gtk.Label("Password strength checker v0.1")
		self.label2 = gtk.Label()
		self.entry = gtk.Entry()

		self.entry.set_text("Please enter your password.")
		self.entry.set_editable(True)

		button1.connect("clicked", self.strength)
		button2.connect("clicked", self.generate)

		hbox.pack_start(button1)
		hbox.pack_start(button2)
		
		table.attach(label1, 0, 2, 0, 1)
		table.attach(self.entry, 0, 2, 1, 2)
		table.attach(hbox, 0, 2, 2, 3)
		table.attach(self.label2, 0, 2, 3, 4)

		window.connect("destroy", lambda w: gtk.main_quit())
		window.add(table)
		window.show_all()

	def strength(self, widget):
		password = self.entry.get_text()
		points = 0
		has_punctuation = 0
		has_number = 0
		has_capital = 0
		has_lower = 0
		is_long = 0

		for i in password:
			if i in string.punctuation:
				has_punctuation = 1

			if i in string.digits:
				has_number = 1

			if i in string.ascii_uppercase:
				has_capital = 1

			if i in string.ascii_lowercase:
				has_lower = 1

			if len(password) >= 8:
				is_long = 1

		total = has_punctuation + has_number + has_capital + has_lower + is_long

		if total == 1:
			strength = "Very Weak"

		elif total == 2:
			strength = "Weak"

		elif total == 3:
			strength = "Moderate"

		elif total == 4:
			strength = "Strong"

		elif total == 5:
			strength = "Very Strong"

		print strength

		self.label2.set_text("Your password strength is: %s" % strength)


	def generate(self, widget):
		new_password = ""
		temp = []
		master_list = []

		master_list.append(string.punctuation)
		master_list.append(string.digits)
		master_list.append(string.ascii_uppercase)
		master_list.append(string.ascii_lowercase)

		print master_list

		for i in master_list:
			print i
			for j in range(random.randrange(1, 5)):
				 temp.append(random.choice(i))
				 print temp

		random.shuffle(temp)

		for i in temp:
			new_password += i

		print new_password
		self.label2.set_text("Password: %s" % new_password)
		self.label2.set_selectable(True)





		



Password()

```

Let me know what you think, thanks

Bodsda
gtk.main()

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-14
> **Bodsda said:**
> Hey Guys,

Just wanted to keep you updated about my progress. The code below is v0.1 of my little password checker. This version includes a new layout and the ability to generate a new Strong or Very Strong password at the click of a button :)

```

			#! /usr/bin/env python

import gtk
import string
import random

class Password:
	def __init__(self):
		
		window = gtk.Window()
		hbox = gtk.HBox(True, 10)
		table = gtk.Table(5, 2, True)
		button1 = gtk.Button("Test Strength")
		button2 = gtk.Button("Generate Password")
		label1 = gtk.Label("Password strength checker v0.1")
		self.label2 = gtk.Label()
		self.entry = gtk.Entry()

		self.entry.set_text("Please enter your password.")
		self.entry.set_editable(True)

		button1.connect("clicked", self.strength)
		button2.connect("clicked", self.generate)

		hbox.pack_start(button1)
		hbox.pack_start(button2)
		
		table.attach(label1, 0, 2, 0, 1)
		table.attach(self.entry, 0, 2, 1, 2)
		table.attach(hbox, 0, 2, 2, 3)
		table.attach(self.label2, 0, 2, 3, 4)

		window.connect("destroy", lambda w: gtk.main_quit())
		window.add(table)
		window.show_all()

	def strength(self, widget):
		password = self.entry.get_text()
		points = 0
		has_punctuation = 0
		has_number = 0
		has_capital = 0
		has_lower = 0
		is_long = 0

		for i in password:
			if i in string.punctuation:
				has_punctuation = 1

			if i in string.digits:
				has_number = 1

			if i in string.ascii_uppercase:
				has_capital = 1

			if i in string.ascii_lowercase:
				has_lower = 1

			if len(password) >= 8:
				is_long = 1

		total = has_punctuation + has_number + has_capital + has_lower + is_long

		if total == 1:
			strength = "Very Weak"

		elif total == 2:
			strength = "Weak"

		elif total == 3:
			strength = "Moderate"

		elif total == 4:
			strength = "Strong"

		elif total == 5:
			strength = "Very Strong"

		print strength

		self.label2.set_text("Your password strength is: %s" % strength)


	def generate(self, widget):
		new_password = ""
		temp = []
		master_list = []

		master_list.append(string.punctuation)
		master_list.append(string.digits)
		master_list.append(string.ascii_uppercase)
		master_list.append(string.ascii_lowercase)

		print master_list

		for i in master_list:
			print i
			for j in range(random.randrange(1, 5)):
				 temp.append(random.choice(i))
				 print temp

		random.shuffle(temp)

		for i in temp:
			new_password += i

		print new_password
		self.label2.set_text("Password: %s" % new_password)
		self.label2.set_selectable(True)





		



Password()

```

Let me know what you think, thanks

Bodsda
gtk.main()
hey Bodsda...nice app....
But you may wanna hide your password as you type......for that u can use.... 
code:
   self.entry.set_visibility(False)

...anyway...gud  app....
I am learning Pygtk tooo.....!! :)

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-14
> **Bodsda said:**
> Hey Guys,

Just wanted to keep you updated about my progress. The code below is v0.1 of my little password checker. This version includes a new layout and the ability to generate a new Strong or Very Strong password at the click of a button :)

```

			#! /usr/bin/env python

import gtk
import string
import random

class Password:
	def __init__(self):
		
		window = gtk.Window()
		hbox = gtk.HBox(True, 10)
		table = gtk.Table(5, 2, True)
		button1 = gtk.Button("Test Strength")
		button2 = gtk.Button("Generate Password")
		label1 = gtk.Label("Password strength checker v0.1")
		self.label2 = gtk.Label()
		self.entry = gtk.Entry()

		self.entry.set_text("Please enter your password.")
		self.entry.set_editable(True)

		button1.connect("clicked", self.strength)
		button2.connect("clicked", self.generate)

		hbox.pack_start(button1)
		hbox.pack_start(button2)
		
		table.attach(label1, 0, 2, 0, 1)
		table.attach(self.entry, 0, 2, 1, 2)
		table.attach(hbox, 0, 2, 2, 3)
		table.attach(self.label2, 0, 2, 3, 4)

		window.connect("destroy", lambda w: gtk.main_quit())
		window.add(table)
		window.show_all()

	def strength(self, widget):
		password = self.entry.get_text()
		points = 0
		has_punctuation = 0
		has_number = 0
		has_capital = 0
		has_lower = 0
		is_long = 0

		for i in password:
			if i in string.punctuation:
				has_punctuation = 1

			if i in string.digits:
				has_number = 1

			if i in string.ascii_uppercase:
				has_capital = 1

			if i in string.ascii_lowercase:
				has_lower = 1

			if len(password) >= 8:
				is_long = 1

		total = has_punctuation + has_number + has_capital + has_lower + is_long

		if total == 1:
			strength = "Very Weak"

		elif total == 2:
			strength = "Weak"

		elif total == 3:
			strength = "Moderate"

		elif total == 4:
			strength = "Strong"

		elif total == 5:
			strength = "Very Strong"

		print strength

		self.label2.set_text("Your password strength is: %s" % strength)


	def generate(self, widget):
		new_password = ""
		temp = []
		master_list = []

		master_list.append(string.punctuation)
		master_list.append(string.digits)
		master_list.append(string.ascii_uppercase)
		master_list.append(string.ascii_lowercase)

		print master_list

		for i in master_list:
			print i
			for j in range(random.randrange(1, 5)):
				 temp.append(random.choice(i))
				 print temp

		random.shuffle(temp)

		for i in temp:
			new_password += i

		print new_password
		self.label2.set_text("Password: %s" % new_password)
		self.label2.set_selectable(True)





		



Password()

```

Let me know what you think, thanks

Bodsda
gtk.main()
In this app gtk.main()  is missing without which the app wont run....but its a gud extension.... :)

---

### Post by r-senior on 2011-06-14
> **Bodsda said:**
> Let me know what you think, thanks
Good job!

One suggestion I would make is to decouple your 'strength' and 'generate' functions from the user interface. Make them work standalone. So, for example, 'strength' would take a password as a parameter and return a strength constant. You'd then have a couple of specific event handler functions that call the relevant functions and translate the return value into strings for the UI:

```

def on_strength_activated(self, widget):
    password = self.entry.get_text()
    password_strength = self.strength(password)
    ...
    # Set text in UI based on return value
    ...

```

This gives you the opportunity to reuse those functions in other situations. Maybe put them in their own module with doctest comments?

---

