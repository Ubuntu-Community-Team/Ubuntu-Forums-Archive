---
title: "Making a web page"
date: 2007-10-19
forum: Programming Talk
---

### Post by CapitanYochua on 2007-10-19
I want to make a web page through a free hosting site. (I've picked x10hosting). And I was wondering what kind of things I should learn to start this task. Preferably something with Python because I already have the intent on learning that. I've heard things about PHP, Apache, MYSQL, etc... And to be honest I'm pretty ignorant about all of that. Any advice, hints, or suggestions would be appreciated. Thank you.

---

### Post by TreeFinger on 2007-10-19
I would suggest starting at the basics. For a webpage this would be creating a simple HTML website with some CSS for styles.

It all depends on what you want your webpage to do.

---

### Post by LaRoza on 2007-10-19
[www.w3schools.com](www.w3schools.com)

Learn XHML, CSS, then look into PHP and Python. I use PHP for my sites, [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home) (Site needs to be updated, will do soon)

---

### Post by pmasiar on 2007-10-19
Web page (graphics) design is very different skill from programming. So it depends where you want to go. it is rare that people excel in both, they require different skills.

For (static) web pages, you have HTML+CSS. Some ppl use javascript for dynamic pages and AJAX, or Flash. Learning this can get you a job.

For dynamic web pages, Python has everything PHP does, and more, so there is hardly any reason to use PHP anymore. If your hosting service does not support Python, switch to one which does.

To learn Python, don't start with dynamic webpages, not even GUI: start with plain old text-based code. Wiki in my sig has plenty of links.

---

### Post by CapitanYochua on 2007-10-19
How do I use python to make plain text sites?

---

### Post by pmasiar on 2007-10-19
You mean plain text programs? Commandline? Just learn Python, links in wiki in my sig.

If you mean static webpages, you don't need Python for that, just HTML.

---

### Post by CapitanYochua on 2007-10-19
Could I use python in the terminal to write and save .html files to upload on my web hosting site?

---

### Post by pmasiar on 2007-10-21
yes. It is matter of simple programming. :-)

You may want to look at any existing templating system before writing your own :-)

---

### Post by CapitanYochua on 2007-10-26
How would I add a python program into a web page with HTML? For example, if I have a program that uses a user input to do some formula, and it spits out the answer. I already have the program written and saved. Now, how do I add this program into my web page or into an HTML document?
-thanks.

---

### Post by slavik on 2007-10-27
as an embedded program the way java can be done? python can't really do that without javascript and a whole lot more programming :)

---

### Post by CapitanYochua on 2007-10-27
Yeah, as an embedded program. What's the point of writing it in Python to begin with if you have to use java? How exactly would you use both to do it? And how could I just host the program for download rather than embed it on the site?

---

### Post by smartbei on 2007-10-27
You may want to take a look at [http://wiki.python.org/moin/WebProgramming](http://wiki.python.org/moin/WebProgramming) for some popular frameworks used in python web development. Also see [http://colorstudy.com/docs/shootout.html](http://colorstudy.com/docs/shootout.html) which has some interesting examples of how to use the different frameworks.

If all you're looking for is a simple way to print to the output of a program to the user's browser:
[http://webpython.codepoint.net/introduction](http://webpython.codepoint.net/introduction) is a tutorial about basic python web programming and also instructs on accessing forms (which you will need to get input from the web page's user usually).

Feel free to ask if you need more help!

Re-reading your previous post, you mention "Yeah, as an embedded program." Python is used as a server-side language, meaning it runs on the server and is absolutely transparent to the web page's user. It is not embedded in the page like JavaScript.

After taking a look at your website, I would first like to mention that it looks like you are off to a good start. Secondly, you may want to take a look at the html tidy extension for firefox, which finds mistakes in the (x)html source of pages you browse to (there were several small things). [https://addons.mozilla.org/en-US/firefox/addon/249](https://addons.mozilla.org/en-US/firefox/addon/249)

---

### Post by airtonix on 2007-10-27
if you want embeded then windows users will miss out. (not that i care)

what you really want to do is get apache to run python like it does with php.

otherwise you have to find a clientside plugin that will work on osx/win2kxpvista/linux/etc/etc/etc/etc

trust me....python is really for use on linux clients....but you can use it in webpages(but only like we already use php/asp/cgi/etc)....but your rollout impact is too large for it to be viable in the fashion that flash or javascript already is.

to get safe realtime feedback from such scripts (which if they were to be exposed on the client as a java app is, posesa security issue) you would need to investigate the use of something like prototype, or mootools javasripting framework to facilitate the flow of data between client and server.

ajaxian is a easy to digest site...so is the mootols site.

any other way has already been tried and examined for that last 20-40yrs....and waht we have now is a great synthesis of that time period.

we dont need a nanny corp to maintain a binary client side framework, we dont need a nanny corp to re-create formatting tecniques that html , css and javascript can do qquite adequately.

what we dooo need is savy web developers. people who understand and appreciate efficient data flows. people who arent going to "meh" themselves into a wet paper bag whislt ensaring everyone else in their brain&^%#$ of a propriatey stupidity.

please excuse my attrotius spelling for i care not to try. fingers are to blame.

---

### Post by CapitanYochua on 2007-10-27
All those links are kind of confusing since I'm not exactly sure what it is that I want to do to begin with.

---

### Post by smartbei on 2007-10-27
Well, you said you have a program that takes user input and spits out some sort of answer. You can use html forms to capture the user's input, access the data through the forms section [here]("http://webpython.codepoint.net/introduction") and then output the data as shown in that same web page, after running it through your function.

Does that clear it up a bit (I hope so :D ).

---

### Post by CapitanYochua on 2007-10-27
Yeah, I get what you are saying. I'm just starting to program, and make web pages. So, the link doesn't make all that much sense to me. I'll reread it some more, and try to figure things out. Thanks.

---

### Post by smartbei on 2007-10-27
Ok, I was interested and having fun looking this up, so I made a small demo page... You can find it running [here]("http://gahl.saraf.org/python/simple_web_page.py")

The actual code for that is:
```

#!/usr/bin/python
import cgi

def main():
	print "Content-type: text/html\n\n" #necessary!!! without this it wont work
	form=cgi.FieldStorage() #initialize the form storage for getting data from the user
	name=form.getfirst("name") #get the name from the user (through the form)
	if name != None:
		name=nameProcess(name) # save processed name
	else:
		name="No name input :(" #no name given...
	
	# This is the actual page:
	print """
	<html>
	<head>
	<title>Name Perioder</title>
	</head>
	<body>
	<h1>%s</h1>
	<form action="" method="get">
	<input type="text" name="name">
	<input type="submit">
	</form>
	</body>
	</html>""" % name #string formatting - insert the name into the page

def nameProcess(orig): #function to be called on user input. Inserts a dot after each letter.
	final=""
	for a in orig:
		final+=a+"."
	return final

if __name__ == "__main__": #checks to make sure that this page isn't included by another. if it is, we wouldn't want it to print the contents of main().
    main()

```

Not the most elegant, but I think it illustrates the basic point.

---

### Post by CapitanYochua on 2007-10-27
That was pretty helpful and neat. (:
I'll look more into it later, and I'll post again.

---

### Post by CapitanYochua on 2007-10-28
Do you mind explaining the code to me that way I can understand exactly what's happening, since I'm new to all of this? Thanks

---

### Post by smartbei on 2007-10-28
Well, here is a pretty precise run-down of what is happening. Note - this assumes that you are somewhat versed in python. If not, read up on some python tutorials. This isn't really advanced stuff, language-wise. If there is something specific you don't understand, don't hesitate to ask. I also use html forms to send data, so you may want to check those out (if you haven't yet already).

**Before Main:**
The line:
```
#!/usr/bin/python
```
Tells whoever is running the program what interpreter to use to process it.

The next line imports cgi, which is a module that I don't know much about, other than the fact that it provides the FieldStorage object so I can access user input through the form.

**The main function:**
The first line prints the header of the page, telling the browser what to do with the rest of the data it receives. In this case, we are sending html, so we put text/html.

The second line initializes the FieldStorage object, which allows us to access user data sent in a form (or rather any data sent by Get or Post).

The third line stores the value in the FieldStorage object which corresponds with the key "name". This is the same name we give to the html input some lines below. Don't be confused by name (attribute) and "name" (value of said attribute, key to data in FieldStorage object).

The fourth line checks if name (the variable in which we stored the value pointed to by "name") is None, the default value returned by getfirst in case no value was sent (this is the first time the user went to the page, etc.). None is the python equivalent to NULL.

If a name was not None, it processes it and stores the value in the same variable. See below for an explanation on that function.

Otherwise, it sets the variable name to a default value ("No name input :(" ).

Then, we print out all of the html for the page (note - not standards-compliant, just hacked together for the example). The only thing to notice is the %s in the <h1>. This is the python way to do string formatting, %s means insert string at that place. Then, at the end you have one % and the variable you wish to replace it with.

Note that I use a triple quote (""") in order to quote multiple lines.
[B]
The nameProcess function:[/B] (takes as input orig, the string to be processed)
The first line initializes the variable that will be returned.

The second line starts a loop (read up on python loops).

The third line adds to final (+=) the current letter (a) and a period (can be whatever).

The last line in the function returns the string final.
[B]
Lastly, [/B]
```

if __name__ == "__main__":
    main()

```
Checks if this file is the file being run, or whether it is being imported by another. (For example, you may want another file to use this file's nameProcess function, but then you probably wouldn't want the main function to run automatically.

Hope that made things clearer. The best way to learn is to try things out, so go ahead and take this code and try to change it to make use of the function you have. Enjoy! :)

---

### Post by slavik on 2007-10-29
could you explain the __name__ variable? what does it get set to and when?

---

### Post by smartbei on 2007-10-29
the __name__ variable is a global python variable, set by the python interpreter for every file loaded (I am pretty sure but may be a little off). If the file loaded was called directly (executed) __name__ is equal to __main__. Otherwise, it isn't. Try printing it out a couple times to see what it holds.

See [http://www.ibiblio.org/g2swap/byteofpython/read/module-name.html](http://www.ibiblio.org/g2swap/byteofpython/read/module-name.html) for some more info, (though not much...).

---

### Post by pmasiar on 2007-10-29
"if __name__ == "__main__": main()" is canonical start of main() in Python code. It allows you to use same module from commandline and also imported to other code: when used as stand-alone, you usually want to do some spacial work to initialize environment, but not do it if imported and environment is set up by calls to proper functions from a caller program.

smartbei, you have good explanation of web app. I [added it to my wiki](http://learnpython.pbwiki.com/WebApplication). Better variable names would help in avoiding confusion, ie calling it user_name, printing label "what is your name?" in the form would help that.

You should mention cgitb module for debugging Python cgi - real lifesaver.

---

### Post by smartbei on 2007-10-29
Your definately right about the variable names - I realized that when writing the explanation - four different references to "name"!

Your right about the debugging module, but I wanted to keep it simple.

Glad you thought my writing worthy :). I will be making a copy of it and in more tutorial-form eventually I think (if I get around to it). I will contact you if I do.

---

