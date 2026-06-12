---
title: "Data Path"
date: 2010-08-25
forum: Programming Talk
---

### Post by worksofcraft on 2010-08-25
During development I kept all my data files in my current working directory and tested my program with the command ./a.out 

However once it all works to my satisfaction I renamed and moved the binary to /usr/local/bin. That folder is my $PATH so I can now use the command from any current folder.

However my application doesn't know where to look for it's data files and I don't know where I should put the different types.

- read only installation files like the .glade file
- read/write data shared by all users
- read/write preference setting for the current user
- user's work files

Well ok for that last category, I do know that the user should be able to choose where they go, but for the others has anyone got recommendations and should I build in fixed directory paths in my application executable?

---

### Post by interval1066 on 2010-08-25
> **worksofcraft said:**
> During development I kept all my data files in my current working directory and tested my program with the command ./a.out 

However once it all works to my satisfaction I renamed and moved the binary to /usr/local/bin. That folder is my $PATH so I can now use the command from any current folder.

However my application doesn't know where to look for it's data files and I don't know where I should put the different types.

- read only installation files like the .glade file
- read/write data shared by all users
- read/write preference setting for the current user
- user's work files

Well ok for that last category, I do know that the user should be able to choose where they go, but for the others has anyone got recommendations and should I build in fixed directory paths in my application executable?

This is a big topic and depends on what kind of application you're writing. If this is a gnome desktop app you'll want to at least be familiar with this info;

[http://developers.sun.com/solaris/articles/integrating_gnome.html](http://developers.sun.com/solaris/articles/integrating_gnome.html)
[http://www.yolinux.com/TUTORIALS/GTK+ProgrammingTips.html](http://www.yolinux.com/TUTORIALS/GTK+ProgrammingTips.html)
[http://ubuntuforums.org/showthread.php?t=1103290](http://ubuntuforums.org/showthread.php?t=1103290)
[http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/)

For your testing you can do whatever you want, but I recommend putting your binaries in a subdirectory off your home directory, pathing that, and letting your installation scripts install stuff to places like /usr/local and associated branches, as appropriate. Again, assuming a gnome application you'll want to become familiar with these functions:

[http://library.gnome.org/devel/glibmm/2.23/group__MiscUtils.html](http://library.gnome.org/devel/glibmm/2.23/group__MiscUtils.html)

---

### Post by worksofcraft on 2010-08-25
OMG that does all seem a little bit convoluted and a whole lot unnecessarily complicated :shock: However thanks for all those links there interval1066, it's appreciated.

I understand why we don't want to clutter our executable folders ($PATH) with data files and there isn't an easy way to determine current execution path anyway. So I looked at what other programs do.

I noticed that the gettext package expects programs to bind their text domain: Usually with hard coded path to /usr/share/locale.
My app is no exception having it's own text domain off the various locales defined there.

Parallel to said locales many applications also maintain their own specific folders in /usr/share. I'll do likewise to stash my .glade file.

I further noticed that for user specific data, many applications maintain a hidden folder in the user's home directory. I'm not particularly keen on that practice.

Although I'm convinced it was all designed rationally, over the years it may have got a bit out of hand :( IMO the whole /etc structure needs to be put to use to define consistent environment target configurations... oh well, for now hard coded paths and a simple tar file will do for me :)

---

### Post by Bachstelze on 2010-08-26
> **worksofcraft said:**
> 
I further noticed that for user specific data, many applications maintain a hidden folder in the user's home directory. I'm not particularly keen on that practice.

And what do you recommend instead? A big folder in /usr chmodded 777 where the data of all users would go? What if I don't want other users to see my data?

---

### Post by nvteighen on 2010-08-26
For data the application uses regardless of who the user is, usual practices are as follow:

1. /etc/<bin name>: Configuration file. If you need more than one file, use a folder.

2. /usr(/local)/share/<bin name>: For other kind of static (i.e. not changing) data needed. I guess you place it under /usr/local if you're using /usr/local/bin for your program (not sure about this).

3. /usr/share/doc/<bin name>: For documentation. I'm not sure if /usr/local/share/doc has been used by someone.

4. /var/cache/<bin name>: For caches and similar data that changes over time. 

The best would be to have a look at those directories and get yourself acquainted to how they are used. In some cases it seems that some flexibility is allowed (using /opt instead of /usr/local and such stuff).

---

### Post by Bachstelze on 2010-08-26
> **nvteighen said:**
> 
In some cases it seems that some flexibility is allowed (using /opt instead of /usr/local and such stuff).

/usr vs. /usr/local depends on the OS.  Most (all?) Linux distributions put everything in /usr, but other systems like the BSDs that have a clear distinction between software in the base system and third-party software use /usr for the former and /usr/local for the latter.

When you compile something from source, or otherwise install it by another means than your OS's package manager, it's better to always put it in /usr/local unless you have a very good reason to.  /opt is good because you can get rid of the software with just a [font=monospace]sudo rm -rf /opt/foo[/font], but that's generally not needed (we have checkinstall and friends).

---

### Post by worksofcraft on 2010-08-26
> **Bachstelze said:**
> And what do you recommend instead? A big folder in /usr chmodded 777 where the data of all users would go? What if I don't want other users to see my data?

I recommend that we have a folder ~/etc where all the user specific package configuration folders go. I don't want them cluttering my home root.

Also I would also recommend that they **not** be hidden: I was very annoyed when I did a backup and found that some essential data from virtualbox had been secretly lurking in a hidden folder.. now I can't restore those virtual machines anymore :(

Anyway, thanks for those other explanations I'll be looking at them in more detail tomorrow :)

p.s. my initial reaction is that we need a system environment target configuration file ... ooops I was about to a suggest a database called "the registry" but thought better of it ;) but yeah in there it would specify things like:

user configuration data: ~/etc/$package
common configuration data: /usr/share/$package
documentation: /dev/null

... well you get the picture, so then even if every vendor and distro has their own peculiar way of doing things at least our computers can be self consistent :)

---

### Post by nvteighen on 2010-08-26
> **Bachstelze said:**
> /usr vs. /usr/local depends on the OS.  Most (all?) Linux distributions put everything in /etc, but other systems like the BSDs that have a clear distinction between software in the base system and third-party software use /usr for the former and /usr/local for the latter.

When you compile something from source, or otherwise install it by another means than your OS's package manager, it's better to always put it in /usr/local unless you have a very good reason to.  /opt is good because you can get rid of the software with just a [font=monospace]sudo rm -rf /opt/foo[/font], but that's generally not needed (we have checkinstall and friends).

Oh, thanks :)

---

### Post by worksofcraft on 2010-08-26
Eventually I worked my way down through a quick assessment of those links that interval066 gave. And most promising did seem the gnome gconf project.

gconftool-2 -R /

gives a good idea how it's being used at the moment and I was appalled! It is full of garbage! :shock:

For instance, dozens of entries relating to "evolution" but I completely uninstalled that package because I much prefer leaving the stuff people send me on my 8G of free storage with gmail where I can get at it from any internet cafe. So why is my gconf data base still brimming with settings for something I don't have... and as consequence plenty more that is of no relevance as well as pages and pages of pointless garbage marked like cdr_type: '*invalid*' locale: `C'... would those entries actually be of any use what-so-ever to anything?

This is so reminiscent of it's Windows counterpart :P

You see the problem with thgis kind of design is that each package has it's own separate set of keys and schemas and so gconf in no way helps to bring any kind of common consistency: e.g. There is **NOTHING** in there where I can specify in general that I want to store user's configuration files in folders off ~/etc :(

---

### Post by worksofcraft on 2010-08-26
So anyway, what I decided to use is as follows

```

#!/usr/bin/python
import sys

# Here etc stands for 'environment target configuration'
class ETC(dict):
	def __init__(self):
		self.configPath = '/etc/etc.etc'
		# simple default
		self.dict = dict ({
			'user_config': '/home/$user/etc/$app',
			'user_data': '.', # work files in current working directory tyvm
			'app_config': '/usr/share/$app',
			'app_data': '/var/$app', # shared user data (e.g. databases)
			'app_docs': '/dev/null' # real documentation is on the www
		})
		try:
			f = open(self.configPath, 'r')
			self.dict = f.read()
			f.close()
		except IOError:
			print >>sys.stderr, 'missing {0}: using defaults!'.format(self.configPath)

		# TODO: expand symbolic $ parameters
		# probably best implemented as a C library module

	# For use by a privileged config app...
	def write(self):
		try:
			f = open(self.configPath, 'w')
			f.write(repr(self.dict))
			f.close()
		except IOError:
			print >>sys.stderr, 'Only superuser can write {0}'.format(self.configPath)

if __name__ == "__main__":
	etc = ETC()
	print repr(etc.dict)
	# test that priviledge required
	etc.write()

```

Hum... waddaya think of that?

---

### Post by Bachstelze on 2010-08-26
> **worksofcraft said:**
> 
```


			'app_docs': '/dev/null' # real documentation is on the www

```


And what if I need the doc when I'm working in a place with no www access, in the train for example? -doc packages exist for a reason. ;) The Unix filesystem layout was designed by people smarter than you and I put together, things are how they are for a reason.

---

### Post by worksofcraft on 2010-08-26
> **Bachstelze said:**
> And what if I need the doc when I'm working in a place with no www access, in the train for example? -doc packages exist for a reason. ;) The Unix filesystem layout was designed by people smarter than you and I put together, things are how they are for a reason.

Lol well you don't know that :D
Just cuz they are from antiquity doesn't make them geniuses. For a start we have the benefit of hind sight and Google too :)

As for the docs... you have choice to ask your sysadmin to edit /etc/etc.etc and make your system put app_docs in /usr/share/doc/$app if that's the kind of thing you like ;)

p.s. Ok I was just joking about the /dev/null... but what would be interesting is to know what kind of paths *WOULD* be really core essentials. I'm thinking the user data entry is redundant and caches and temp files is self evident, but we could define a consistent place for logfiles... and who knows what else?

---

### Post by worksofcraft on 2010-08-27
After thinking about it for a bit I decided this is actually worth doing and Ima gunna make C library and find out how to incorporate it in Python as well...

However environment variables like $HOME and $USER just aren't good enough. I mean you can set them to whatever you want and even unset them all together :shock:

Also I don't want to require argv[0] from the main... so here is my code to get user name and exe name in a kind of fool proof way I hope...

```

#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>

void show_exename() {
	pid_t pid = getpid(); // get our process id
	char cmdfilestr[100]; // some space to stash strings
	char cmdstr[100];
	char *exename; // to search the commond line
	FILE *f; /// to read the /proc files

	sprintf(cmdfilestr, "/proc/%d/cmdline", pid);

	f = fopen(cmdfilestr, "r"); // read pretend file
	fgets(cmdstr, sizeof cmdstr, f); // consists of command only without params
	fclose(f);

	// find end of command string
	for (exename=cmdstr; *exename && (exename < &cmdstr[sizeof cmdstr]); ++exename);
	// search backwards for / cuz we want to omit the path
	while (exename > cmdstr) if (*--exename == '/') {
		++exename; // skip that slash
		break;
	}
	
	printf("the exename is: %s\n", exename);
}

int main(int argc, char **argv) {
	show_exename();
	// if you use sudo to run this, then password file getuid and geteuid
	// both say your name is 'root', but login stays unchanged!
	return printf("the username is: %s\n", getlogin());
}

```

If you see any problems in what I'm doing well critical feedback is actually appreciated here ;)

---

### Post by worksofcraft on 2010-08-27
A format string extracts parameters from a dictionary and converts them into text. For instance in traditional C printf the "dictionary" is the variable length parameter list that follows the format specifier. The indexing in the dictionary is limited to sequential iteration.

Enhanced versions of formatting, like boost library and .net allow indexing of the dictionary with integers as primary key.

Even more advanced is Python's ability to use string indexes.

In this "etc config file" application the format strings are the ones read from the file and the dictionary is a conceptual set of system parameters. The index is a string, an identifier of the parameter and so Python formats would seem a good place to start.

To make it more flexible I want to add an optional domain specifier, so that we can give the context of the identifier: login_name as given by the system or login_name as given by the environment strings... or perhaps even login name as extracted from a simple MySQL database and so on.

... and then basically merge that with the original sort of format specifications that allow the representation (width, justification, precision) to be controlled.

There I hope that's more intelligible now what I was talking about :)

---

### Post by nvteighen on 2010-08-27
Multireplying! :D

> **worksofcraft said:**
> 
For instance, dozens of entries relating to "evolution" but I completely uninstalled that package because I much prefer leaving the stuff people send me on my 8G of free storage with gmail where I can get at it from any internet cafe. So why is my gconf data base still brimming with settings for something I don't have... and as consequence plenty more that is of no relevance as well as pages and pages of pointless garbage marked like cdr_type: '*invalid*' locale: `C'... would those entries actually be of any use what-so-ever to anything?

This is so reminiscent of it's Windows counterpart :P


Yes, it is reminiscent of the infamous Windows Registry and it's one of the best arguments KDE fans have against GNOME fans like me :( (KDE just creates ~/.kde and places everything there). But, the main and key difference with the Windows Registry is that GNOME is only a desktop environment and not the system itself, so corrupting a gconf key or leaving a dead key is a minor issue... while a dead registry key in Windows can make some stuff be uninstallable (e.g. a dead McAfee key can lead to make another AV be uninstallable).

> **worksofcraft said:**
> So anyway, what I decided to use is as follows

```

#!/usr/bin/python
import sys

# Here etc stands for 'environment target configuration'
class ETC(dict):
	def __init__(self):
		self.configPath = '/etc/etc.etc'
		# simple default
		self.dict = dict ({
			'user_config': '/home/$user/etc/$app',
			'user_data': '.', # work files in current working directory tyvm
			'app_config': '/usr/share/$app',
			'app_data': '/var/$app', # shared user data (e.g. databases)
			'app_docs': '/dev/null' # real documentation is on the www
		})
		try:
			f = open(self.configPath, 'r')
			self.dict = f.read()
			f.close()
		except IOError:
			print >>sys.stderr, 'missing {0}: using defaults!'.format(self.configPath)

		# TODO: expand symbolic $ parameters
		# probably best implemented as a C library module

	# For use by a privileged config app...
	def write(self):
		try:
			f = open(self.configPath, 'w')
			f.write(repr(self.dict))
			f.close()
		except IOError:
			print >>sys.stderr, 'Only superuser can write {0}'.format(self.configPath)

if __name__ == "__main__":
	etc = ETC()
	print repr(etc.dict)
	# test that priviledge required
	etc.write()

```

Hum... waddaya think of that?

There's a huge mistake there. file.read() always returns a string and even though that string is the repr of a dictionary, etc.dict will still be a string after the file is read... For worse, **print repr(etc.dict)** shows you the "correct" output just because the repr of a string is the string itself with quotation marks... a string whose content looks like a dictionary :P

If you don't believe me, do **type(etc.dict)**.

There are many ways for serializing and deserializing a dictionary into a file. This is one that uses a simple CSV format:
```

def dict_to_file(filename, obj):
    f = open(filename, "w")
    
    for entry in obj.keys():
        f.write("%s,%s\n" % (entry, obj[entry]))

    f.close()

def file_to_dict(filename):
    f = open(filename, "r")
    mydict = {}

    # Maybe a regexp would be better, but I just don't know how to use them in
    # Python... I'd know how to do this in Perl, though...

    lines = f.read().split("\n")[:-1] # Because the last line will be empty
    f.close()

    for line in lines:
        values = line.split(",")
        mydict[values[0]] = values[1]

    return mydict

def main():
    ex = {'a':'b', 'c':'d', 'e':'f'}
    filename = "test"

    # Maybe a wrapper should take care of this, but well, this is just an
    # example
    try:
        dict_to_file(filename, ex)
    except IOError, e:
        print "Some IO error happened... %s" % e

    try:
        the_dict = file_to_dict(filename)
    except IOError, e:
        print "Some IO error happened... %s" % e

    print "ex: %s\nthe_dict: %s" % (ex, the_dict)
    print "type(ex): %s\n type(the_dict): %s" % (type(ex), type(the_dict))

if __name__ == "__main__":
    main()

```

Of course, you could use regexps, the configparser module, whatever. This is just an example that may be easily used in your code.

> **worksofcraft said:**
> After thinking about it for a bit I decided this is actually worth doing and Ima gunna make C library and find out how to incorporate it in Python as well...

However environment variables like $HOME and $USER just aren't good enough. I mean you can set them to whatever you want and even unset them all together :shock:


That's not an issue... well... actually a good reason why stuff is done as we told you is that it avoids these issues. But nevertheless, $HOME, $USER, etc. are information the program uses and it's not responsible for. If the user does stupid things with those variables and expects everything work well no matter what, then it's the user's problem.. you can't do anything against that.

---

### Post by worksofcraft on 2010-08-27
Thanks for all that good feedback :)

> **nvteighen said:**
> Multireplying! :D
GNOME is only a desktop environment and not the system itself, so corrupting a gconf key or leaving a dead key is a minor issue...


Very good point. Infact so good, it's actually **too** good: This config stuff has to work also on servers that don't have gnome installed... so that's gconf disqualified straight away :(


> **nvteighen said:**
> 
There's a huge mistake there. file.read() always returns a string and even though that string is the repr of a dictionary, etc.dict will still be a string after the file is read... For worse, **print repr(etc.dict)** shows you the "correct" output just because the repr of a string is the string itself with quotation marks... a string whose content looks like a dictionary :P


OMG I see what you mean. These interpreted languages are just full of treachery... what with creating variables of indeterminate type on the fly :shock: Whatever happened to type safe IO?

Also thanks for that code I'll experiment with it a bit :)
Ultimately I don't want to implement it in Python because I want to have it as a C library and then link it into Python, or C or C++...

Incidentally my C code above was also a rapid prototype... using things like sprintf are just asking for trouble when buffers overflow. I've made a safe version now. Is in attached tar file for anyone who wants to get program name and/or user name without trusting environment variables.

> **nvteighen said:**
> 
That's not an issue... well... actually a good reason why stuff is done as we told you is that it avoids these issues. But nevertheless, $HOME, $USER, etc. are information the program uses and it's not responsible for. If the user does stupid things with those variables and expects everything work well no matter what, then it's the user's problem.. you can't do anything against that.

I know, on a personal computer you are right, but elsewhere it's too open to hacking... malevolent users injecting strings into programs to bypass what their administrators have configured.

---

### Post by worksofcraft on 2010-08-27
Following on from my post 14 of this thread that I totally revised so it make more sense to casual reader.

I understand the logic of separating the representation of data from the submission of data for output: The programmer knows what he/she wants to display, but the translator or the end user know how they want it to appear... analogous to separating the HTML and the CSS if you're into web page design.

So now I'm concerned that I fail to see any merit in output streams. They appear to be a seriously retrograde step putting the onus of selecting actual display into so called "manipulators" and back as a burden on the programmer :shock:
Don't they preventing the output being adapted to user locale and force predetermined sequence of what is displayed?

My question is before I get too carried away with my new design: What's good about streams and stream manipulators?

.. and yes I'm aware of type safe output, but than can be done with format strings too. It was just the old C printf way that was a bit negligent there.

---

### Post by nvteighen on 2010-08-28
> **worksofcraft said:**
> 
OMG I see what you mean. These interpreted languages are just full of treachery... what with creating variables of indeterminate type on the fly :shock: Whatever happened to type safe IO?


Treachery? Never thought of it that way :D The nice thing of dynamic environments is that you can make the same code behaive differently depending on the object's type with much less code that in static typed languages like C++. Think of it as having polymorphism by default :P

I suggest you look at my PycTacToe project (link in my sig) and see how much stuff is created on the fly with unknown type :)

And type safe IO... Well, that's not an issue in Python as all IO operations are done using strings: Type safety by default. In other words, you don't ever get an integer 10 as input, but you get a string "10". This means you'll have to convert that to the desired type (e.g. int("10")) but it's quite good. Then, for output, you may write a __str__ method that returns the string "equivalent" of your custom class.

By the way, don't call repr() for printing stuff. print automatically calls str() to convert whatever you have to the string "equivalent". repr() instead returns the text representation of an object you see when evaulating an object in the interpreter.

> 
Incidentally my C code above was also a rapid prototype... using things like sprintf are just asking for trouble when buffers overflow. I've made a safe version now. Is in attached tar file for anyone who wants to get program name and/or user name without trusting environment variables.


I'm not sure if that makes any sense. Ok, it's a clever piece of code, but too paranoid to my taste. Again, I think you are not responsible of whatever changes the environment variables may suffer... Not trusting them because they could be tampered is like not trusting glibc because someone could have replaced it with a version in which printf() does something bad. IMHO, that's the sysadmin's responsability... your responsability is to care about any security flaw *your* code may expose. Otherwise, following your argument to the end would lead you to write your very own OS... and not distribute it because users would also not be allowed to trust your code either.

We even trust proprietary code blindly... Why not trust Free Software that you can always check what it does if you're in doubt? ;)

---

### Post by CptPicard on 2010-08-28
Uh... in all languages I know that have any kind of a type system, while you *create* some value, its type really is not indeterminate... :) variable bindings however may not enforce the referred object's type, as in Python.

---

### Post by StephenF on 2010-08-28
> **CptPicard said:**
> variable bindings however may not enforce the referred object's type, as in Python.
Variable bindings are places in Python. You can put an object on a shelf. The shelf does not become a copy of the object or change it in any way.

---

### Post by CptPicard on 2010-08-28
I'm not sure I understand what you mean, StephenF... what I was saying is that Python's objects have types (in particular when being created, the type is not "arbitrary"), but Python's "variables" (which are bindings to these objects) do not carry the type information, which is inherent to the object.

---

### Post by worksofcraft on 2010-08-28
> **nvteighen said:**
> Treachery? Never thought of it that way :D The nice thing of dynamic environments is that you can make the same code behaive differently depending on the object's type with much less code that in static typed languages like C++. Think of it as having polymorphism by default :P

I suggest you look at my PycTacToe project (link in my sig) and see how much stuff is created on the fly with unknown type :)


I tell Python interpreter that my ETC class derives from the dictionary class **dict** which is a built in type... and then I call the constructor of that dict base class. I never suspected it would be turning it into a string behind my back :shock:

p.s. thanks for that PycTacToe... I didn't manage to beat it's AI yet but more importantly I think I can learn a lot about python and also how to make distributions by seeing how you did yours :)

> **nvteighen said:**
> 
By the way, don't call repr() for printing stuff. print automatically calls str() to convert whatever you have to the string "equivalent". repr() instead returns the text representation of an object you see when evaulating an object in the interpreter.


You see I could type that exact same string at the Python command prompt and it would create a proper **dict** object form it, so why can't it do that when I read it from a file? It's simply "unreasonable" behavior IMO :confused:


> **nvteighen said:**
> 
your responsability is to care about any security flaw *your* code may expose. Otherwise, following your argument to the end would lead you to write your very own OS... and not distribute it because users would also not be allowed to trust your code either.

We even trust proprietary code blindly... Why not trust Free Software that you can always check what it does if you're in doubt? ;)

I'm often making mistakes and so unaware of corrupting things that might be needed elsewhere and then things do go wrong when I least expect! I just thought it be nice to get the data straight from it's source, thinking of the problems SQL injection caused because PhP and MySQL designers were so trusting.

e.g. Hackers put in someone else's name and include a closing quote and the SQL to ask for their password and then an opening quote... to feed that password straight back into the login and hey... they can be whoever they like...

---

### Post by worksofcraft on 2010-09-03
Ah well I got my draft prototype... You see it's configuration file parsing and a hierarchical database and internationalizable output formatting all rolled into one simple set of objects... look here is how it works in my first test program:

```

int main() {
	// traditional output of items by using their operator charptr
	// note: for the following it is allocated in dynamic memory which is deleted by the distructor
	// so since these are anonymous variables they last only for duration of this statement.
	printf("app = %s, path = %s, login = %s\n",
		(charptr) appname_item(), (charptr) exepath_item(), (charptr) loginname_item()
	);

	// this item parses it's file into a map of items which also will be deleted by the destructor
	etc_item Etc("etc.etc");

	// locate an item in the container. Note reference parameter cannot be NULL,
	// so if it isn't found you get an item called (Void)
	cout << "LocalePath = " << (charptr) Etc["LOCALE"] << endl;

	// now this is the cool bit: we get the format to identify the parameter in the container
	// see the extra $ bit in between the traditional C %s format.
	// Here also I'm using my FORM macro to create annonymous output buffer space of 256 bytes
	// not on the heap, because we don't need it beyond this statement.
	cout << Etc.FORM("indexed from the format we get %LOCALE$s", 256) << endl;
	
	// We can also extract the format string known as USERETC from one container
	// and apply it to format a specific item...
	cout << loginname_item().FORM(Etc["USERETC"], 256) << endl;

	// ... and that formatted item itself could be a container in which the format identifies
	// what we want!
	// e.g. use the HOME variable from the environment container 
	//  - I create an annonymous instance of env_item then the entry known as USERLOG
	// from my Etc config file specifies to use that as one of it's parameters
	cout << env_item().FORM(Etc["USERLOG"], 256) << endl;

	return 0;
}

```

gives output:

```

$ ./a.out
app = a.out, path = /home/cjs/Desktop/etc, login = cjs
LocalePath = /usr/share/locale
indexed from the format we get /usr/share/locale
/home/cjs/etc
/home/cjs/log

```

You might wonder about the strange syntax in the etc config file... but that's because I made it a type safe backward compatible extension of the good old printf formats we all know and love ;)

```

locale=/usr/share/locale # localization happens here
useretc = /home/%s/etc # user config files apply to the login id
userlog = %HOME$s/log # log file path by using HOME apply to environment 

```

I'll release the source when I tidied up some loose ends. ATM  it's about 500 lines of C++ but a lot is comments and diagnostics

---

### Post by dwhitney67 on 2010-09-03
> **worksofcraft said:**
> ...
Is in attached tar file for anyone who wants to get program name and/or user name without trusting environment variables.


What is wrong with examining environment variables?  One can play around with the USER env, but that will not change their permissions level.  In other words, changing the variable to something other than their real user-id buys nothing.

As for the executable name, your program offers no more insight than if one had merely examined argv[0].  So what is the point of getexename_r()?  If you want the full-path to the executable, as entered by the user, then make the following change:
```

#if 0
        // scan command line for /
        for (p = buf; *p && (p < &buf[bufsize]);) {
                if (*p++ == '/') exename = p; // leave a marker just past the last the last /
        }
#else
        p = buf;
#endif

```

Of course, the full-path of the executable name is generally of no interest because one can't trust the result.  After all, the executable program could lie within one's PATH, thus obviating the need for the user to type in a full path name in the first place.  Thus all you would yield would be the equivalent of argv[0].


P.S.  Don't include <asm-generic/errno-base.h>; include <errno.h> or <cerrno> for C++.

P.S. #2   Too many comments in the code!  Most of the stuff you comment on are obvious.  Try relegating the comments to something more practical, like the API.

---

### Post by worksofcraft on 2010-09-03
> **dwhitney67 said:**
> What is wrong with examining environment variables?...


Nothing wrong with it. In fact very useful. However, sometimes programs do need to run with root permissions on behalf of a user who doesn't have them normally and then you might want to make sure to use the correct login id and not some fake one set in the environment.

The exe path as obtained from /proc/PID/exe is not from the command line but the actual path to the executable regardless how it is found. I agree I'm not sure what use it is, but thanks for that code. I had written something similar meanwhile to split the path from the file name.

Also thanks for that tip about header files I'll check which one has the right constants defined :)

p.s. Yeah the way I write code is to write the comments first and then fill the code in when I know what I want to do. I agree I need to delete more comments in the future ;)

---

### Post by dwhitney67 on 2010-09-03
> **worksofcraft said:**
> Nothing wrong with it. In fact very useful. However, sometimes programs do need to run with root permissions on behalf of a user who doesn't have them normally and then you might want to make sure to use the correct login id and not some fake one set in the environment.

This is irrelevant; if the program is being run with root privileges, then the user is root... period.

> **worksofcraft said:**
> 
The exe path as obtained from /proc/PID/exe is not from the command line but the actual path to the executable regardless how it is found. I agree I'm not sure what use it is, but thanks for that code. I had written something similar meanwhile to split the path from the file name.

There are uses for the path to the executable name; what I was inferring earlier was that your code was not deducing this properly.  It is no better than examining argv[0].  Examine the actual file pointed to by /proc/<pid>/exe, and then you will have something useful.  Personally I would suggest that you use readlink().

> **worksofcraft said:**
> 
Also thanks for that tip about header files I'll check which one has the right constants defined :)

There's no need to check on anything; for C programming, the one and only file to include for referencing errno constants is <errno.h>.

---

### Post by worksofcraft on 2010-09-03
> **dwhitney67 said:**
> This is irrelevant; if the program is being run with root privileges, then the user is root... period.


```

$> g++ -DTEST proc_id.c
$> sudo ./a.out
[sudo] password for cjs: 
prog = a.out, path = /home/cjs/Desktop/etc
the login username is: cjs
command is a.out, path .

```

... period? Whatever... I'll update that archive with the proper version forthwith. It has a .h file now ;). It's just a very little part of my main project here.

p.s. for those who missed it, the archive is attached to post 16 of this thread.

---

### Post by dwhitney67 on 2010-09-03
> **worksofcraft said:**
> 

... period? Whatever... 

Compile this C program (using gcc):
```

#include <stdio.h>

int main()
{
   FILE* fp = popen("id -un", "r");

   if (fp)
   {
      char buf[15] = {0};

      fgets(buf, sizeof(buf), fp);

      fprintf(stdout, "Running as: %s", buf);
      fprintf(stdout, "User id is: %s\n", getenv("USER"));

      pclose(fp);
   }

   return 0;
}

```
Then run it, once as yourself, then again using sudo.

P.S.  The login username is irrelevant.  It's the permission's level that you should be focused on.

---

### Post by nvteighen on 2010-09-03
> **worksofcraft said:**
> ```

$> g++ -DTEST proc_id.c
$> sudo ./a.out
[sudo] password for cjs: 
prog = a.out, path = /home/cjs/Desktop/etc
the login username is: cjs
command is a.out, path .

```

... period? Whatever... I'll update that archive with the proper version forthwith. It has a .h file now ;). It's just a very little part of my main project here.

p.s. for those who missed it, the archive is attached to post 16 of this thread.

Why do you asume 'sudo' will be used? Why not 'su' (there your code would fail miserably)? What if someone executes this from single-user mode? More important: Should you care about that? No.

Sometimes, the less assumptions you do, the better: I already told you this, but I guess dwhitney67, in all his experience, has rephrased it much better in a little C program :P Leave the OS do its work: You're not mantaining anything on the GNU project nor the Linux kernel, so, just care about what your application is doing.

---

### Post by worksofcraft on 2010-09-03
> **nvteighen said:**
> Why do you asume 'sudo' will be used? Why not 'su' (there your code would fail miserably)? What if someone executes this from single-user mode? More important: Should you care about that? No.

Sometimes, the less assumptions you do, the better: I already told you this, but I guess dwhitney67, in all his experience, has rephrased it much better in a little C program :P Leave the OS do its work: You're not mantaining anything on the GNU project nor the Linux kernel, so, just care about what your application is doing.

It is called exploring and learning about Linux. It started as a bit of code to find the path to the executable and I thought "What else can I get from the system?" I never heard of popen b4 and just wanted some sample data I could use as an indexable container for my project.

dwhitney67 code is instructive and interesting. It is similar yet different and so would serve alternative purpose. As you can see from this output:
```

cjs@cjs-ubuntu:~/Desktop/etc$ g++ popen.c
cjs@cjs-ubuntu:~/Desktop/etc$ ./a.out
Running as: cjs
User id is: cjs
cjs@cjs-ubuntu:~/Desktop/etc$ export USER=hacker_the_pirate
cjs@cjs-ubuntu:~/Desktop/etc$ ./a.out
Running as: cjs
User id is: hacker_the_pirate
cjs@cjs-ubuntu:~/Desktop/etc$ sudo ./a.out
[sudo] password for cjs: 
Running as: root
User id is: root
cjs@cjs-ubuntu:~/Desktop/etc$ 

```

---

### Post by dwhitney67 on 2010-09-03
> **worksofcraft said:**
> 
```

...
cjs@cjs-ubuntu:~/Desktop/etc$ export USER=hacker_the_pirate
cjs@cjs-ubuntu:~/Desktop/etc$ ./a.out
Running as: cjs
User id is: hacker_the_pirate
... 

```

As you see from above, "hacker_the_pirate", albeit a funny name, really is not the user running the program.  In fact, since this user does not exist on your system, it would never be running a program.

Btw, popen() is "pipe-open"; it is used to issuing commands similar to using system(), yet it returns a file descriptor to the pipe so that standard-out and -err from the executed command can be read, using fgets() or other similar function.

---

### Post by trent.josephsen on 2010-09-03
> **worksofcraft said:**
> It is called exploring and learning about Linux. It started as a bit of code to find the path to the executable and I thought "What else can I get from the system?" I never heard of popen b4 and just wanted some sample data I could use as an indexable container for my project.

The correct solution, in both cases, is "don't do that".  There is no particularly useful information to be gained from whatever $USER is set to, because users can set them on the fly as already demonstrated.  There is also no particularly useful information to be gained from finding the path to the executable, because it's non-portable and won't necessarily give you what you want.

Moral of the story:  Let the user do whatever stupid things he wants.  Environment variables are part of the input to your program; use them appropriately, and deal with unexpected values the same way you deal with other types of unexpected input.  (In particular, don't try to use $USER to measure privilege level, but I think others have already covered that.)

---

### Post by worksofcraft on 2010-09-03
> **trent.josephsen said:**
> The correct solution, in both cases, is "don't do that".  There is no particularly useful information to be gained from whatever $USER is set to...

IMO blanket statements like that are not actually productive. 

Writing a system administrator tool one might for instance want to use the user's login name to record a file by his/her name somewhere in a protected area.

Recording in a file identified by whatever their $USER variable is set to, or identifying them all as 'root' because you need root permission to write there really isn't very helpful.

Perhaps a hacker would set $USER=../../boot/vmlinux or whatever nasty trickery it takes to overwrite your kernel with his/her log file?

The path to the executable could be used amongst others to derive an appropriate place to store application configuration files e.g. it's .glade xml gui definition.

IMO this information could come in very handy for my configuration file processing tools and using them is optional.

---

### Post by Some Penguin on 2010-09-04
That's what getlogin_r and getuid are for.

---

### Post by worksofcraft on 2010-09-04
I know
The code I wrote was for getting the path and name of the executable.

Anyway enough of this.

... back to part of the real issue: Inadequacies of existing format facilities so extending them to let format more fully specify the data to use. Let's forget about those config file paths to files that depend on login id's and current application names or what not... it's a bit boring and trivial.

As we saw in [http://ubuntuforums.org/showthread.php?t=1549724](http://ubuntuforums.org/showthread.php?t=1549724) an example might be to present ordinal numbers. The English programmer is blissfully unaware of all the subjunctives and gender types that might have to be expressed and at best can present the "st" from "1st" to be pluralized by dngettext() with no further distinctions.

Now I've moved this dngettext call into the format itself.

"You are the %2$d%1/_ordinal/st$2$s person to..."

Here the traditional % introduces the format place holder, the 2 identifies second parameter supplied, the d says to show it in decimal and the $ separate the paths as per the standard extended  C/C++ formatting syntax.

Then I'm accessing the first parameter (it is an item of my generic "dngettext container" class in this case).
There we index the word "st" in the _ordinal domain and index that with our second parameter once again to give the correct plural form.

So what's the problem you may be wondering?

The problem is ambiguity! Just in case for some strange reason the programmer decides to put a / or a $ straight after my "s" string representation selector... it suddenly looks like yet another parameter reference. One with name of "s" to be precise :(

So do I really want to remain backward compatible?
Do I make it illegal to butt an $ onto a format specifier, or perhaps instead I try extending the syntax of Microsoft .net formats, boost or even the Python ones? IDK... decisions how to make them :confused:

---

### Post by nvteighen on 2010-09-04
> **worksofcraft said:**
> 
... back to part of the real issue: Inadequacies of existing format facilities so extending them to let format more fully specify the data to use. Let's forget about those config file paths to files that depend on login id's and current application names or what not... it's a bit boring and trivial.

As we saw in [http://ubuntuforums.org/showthread.php?t=1549724](http://ubuntuforums.org/showthread.php?t=1549724) an example might be to present ordinal numbers. The English programmer is blissfully unaware of all the subjunctives and gender types that might have to be expressed and at best can present the "st" from "1st" to be pluralized by dngettext() with no further distinctions.

Now I've moved this dngettext call into the format itself.

"You are the %2$d%1/_ordinal/st$2$s person to..."

Here the traditional % introduces the format place holder, the 2 identifies second parameter supplied, the d says to show it in decimal and the $ separate the paths as per the standard extended  C/C++ formatting syntax.

Then I'm accessing the first parameter (it is an item of my generic "dngettext container" class in this case).
There we index the word "st" in the _ordinal domain and index that with our second parameter once again to give the correct plural form.

So what's the problem you may be wondering?

The problem is ambiguity! Just in case for some strange reason the programmer decides to put a / or a $ straight after my "s" string representation selector... it suddenly looks like yet another parameter reference. One with name of "s" to be precise :(

So do I really want to remain backward compatible?
Do I make it illegal to butt an $ onto a format specifier, or perhaps instead I try extending the syntax of Microsoft .net formats, boost or even the Python ones? IDK... decisions how to make them :confused:

My god...

You could use escape characters... For example, I guess you know in a regular printf(), when you want to use the '%' character, what you type in the format string is '\%' so the % isn't interpreted as a format specifier but printed as the '%' character.

But we already discussed about the really difficult issues of this idea you have. It isn't impossible in theory, but it'll require very complex code that teaches your program the aspects of English grammar relevant to this issue... which are pretty much unclear even in grammar theory.

And anyway, what you try to do seems to be more suited to Lisp macros rather than to Python... :D

---

### Post by worksofcraft on 2010-09-04
lol yeah it's only example of how to use the same format parsing for a whole host of things, from parsing configuration files, substituting parameters, querying databases and formatting output... data of course.

So yes I agree I've done what you suggest and basically use a %$ to put a $ character right after a format place holder now... shouldn't be too many conflicts.

Now what got me worried is what it looks like in the code:

```

   cout << array_item(
      &int_item(3),
      &dngettext_item("_ordinal")
   ).form2(
      "This is my %0$d%1/st$0$s format!"
   ) << endl;

```

- creates a container of type "array_item".
- packs it with two data items that we want to output:
1. an int_item (holding the value 3 here)
2. a dngettext_item which, I suppose is best compared to a data base:
   returning a string from the _ordinal table in response to a numerical key,
   and an input attribute string.(*)

- form2 method is invoked and that uses the format to display the data that is held in the anonymous item of class array_item. The format specifies to display parameter 0 from the container in decimal form: %0$d, followed by parameter 1 indexed by string "st" from the format and parameter 0 from the container represented by a string: %1/st$0$s...

Using standard gettext the "translator" has the ability to translate said format into anything he/she wants and thereby can call any set of parameters supplied in the container as well as specify which tables and keys to use in the dngettext "database"

Well it works but IDK perhaps it's too complicated to use?

---

### Post by trent.josephsen on 2010-09-04
> **worksofcraft said:**
> Writing a system administrator tool one might for instance want to use the user's login name to record a file by his/her name somewhere in a protected area.

Recording in a file identified by whatever their $USER variable is set to, or identifying them all as 'root' because you need root permission to write there really isn't very helpful.

Perhaps a hacker would set $USER=../../boot/vmlinux or whatever nasty trickery it takes to overwrite your kernel with his/her log file?
Which is exactly why you don't use $USER for that.  Thank you for making my point so aptly.  (The only program I can think of that uses $USER visibly is NetHack, for naming new players.)

> The path to the executable could be used amongst others to derive an appropriate place to store application configuration files e.g. it's .glade xml gui definition.
Okay, but what about the guy who links the executable under a different name in $HOME/shortcuts?  Will everything break?  Will he suddenly lose all his configurations?  Will you suddenly litter his $HOME with configuration files, or worse, overwrite something already there?  Paths to global config files should be determined at compile time and given sane defaults, like /usr/share/something.  Paths to per-user configurations should go in $XDG_CONFIG_HOME/something.  Insist on breaking convention for no reason and you'll only succeed in annoying your users.  Have fun.

---

### Post by worksofcraft on 2010-09-04
> **trent.josephsen said:**
> Which is exactly why you don't use $USER for that.  Thank you for making my point so aptly.  (The only program I can think of that uses $USER visibly is NetHack, for naming new players.)


You are welcome, and thank you for sharing the same opinion on this :) 

> **trent.josephsen said:**
> 
Okay, but what about the guy who links the executable under a different name in $HOME/shortcuts? ...

Well that is a very good question. One way to find out is to try it ;)
```

$> ./a.out
app = a.out, path = /home/cjs/Desktop/etc, login = cjs
$> sudo cp a.out /bin
$> which a.out
/bin/a.out

$> cd /usr/local/bin
$> sudo ln /bin/a.out
$> cd ~
$> which a.out
/usr/local/bin/a.out
$> a.out
app = a.out, path = /bin, login = cjs
$> sudo rm /bin/a.out
$> which a.out
/usr/local/bin/a.out
$> a.out
bash: /bin/a.out: No such file or directory

```

I'm a bit confused as I wanted a hard link not a symbolic one... However sometimes people do not want to install in a system folder... perhaps they want to trial a beta version installed in their home directory and leave the stable one in the system folder undamaged. So hard coded paths are not that good either.

p.s. anyway the archive has now been moved to
[http://code.google.com/p/speaknumber/downloads/list](http://code.google.com/p/speaknumber/downloads/list)

under the name "conform.tar"

---

### Post by worksofcraft on 2010-09-04
I just realized of course you won't have my experimental _ordinal.mo localization domain installed so the last output won't be correct ordinal's for English either but it shows default behavior when no locale defined.

I realized I need two format methods: one for things that don't get translated to foreigneeze and one that does, so now I named the formatting method that gets translated "gettext". This is implicitly recognized by the gettext tools for string extraction, yet doesn't conflict because it's a method and thus all those irksome "_()" macros become superfluous :)

I'll include my .mo files later so you can see the iternationalization & localization in action but first I want to sort out some of syntax. I mean it simple enough in English:

An item is either a string or a number or a container of items.

But the C++ compiler seems to have difficulties to understand that. Somehow I have to simulate polymorphism in the constructors and then I can just use strings and numbers and items without having to explicitly coerce them into a type... I suppose that's what you get for free in languages like Python but I only want it happening where an "item" is expected... not everywhere :shock:

p.s. as a side issue this is also about design methodology, you see I used neither "bottom up" nor "top down" it's more a kind of "sideways on" where I built a very thin implementation all the way from top to bottom to show the principle and then fill in all the missing features to widen it's applicability. Meh IDK I'm sure some professor has a name for this methodology cuz it seems to work quite well :)

---

### Post by dwhitney67 on 2010-09-04
What has been lost in translation is what in pray tell are you trying to accomplish?

Even if it is a new method to slice bread into ever more delicious manta, would I ever use this tool?  Well, at least not tonight.  Cheers.

---

### Post by worksofcraft on 2010-09-04
> **dwhitney67 said:**
> What has been lost in translation is what in pray tell are you trying to accomplish?

Even if it is a new method to slice bread into ever more delicious manta, would I ever use this tool?  Well, at least night tonight.  Cheers.

An implementation of the universal "item" class ;)

- An item is a string or a number or a collection of items

- an item has a format method so you can send it to an output stream as text.

- items themselves can be used as formats and the contents of the formats can supply more items for use in this process.

- items are polymorph so they can obtain their data from... well whatever you program for that class.

Applications are endless... obtaining configuration data from, substituting parameters in strings, enhanced formatting abilities with integral internationalization, data base access... all through one consistent and very simple interface:

item.form(FormatString)

---

### Post by dwhitney67 on 2010-09-04
I guess I not in the market for that.

You "speak" just like Alan Greenspan; very sure of yourself, yet very vague.

In C++, if I want to display an object to the terminal (very schoolish, by the way... nobody really does this for professional apps)... something like this would be done:
```

std::cout << myObj << std::endl;

```
where myObj is some type of object that I have created, or perhaps an STL string.  If it were an STL string, or an int, or other trivial data item, then I would not have to worry about implementing a method that handles the operator<<() interface.

In other cases, say retrieving data from a database, a heterogeneous class object could be developed that presented the data in the format that is desirable to the application.

Results from a database query are always given in string-format, regardless of the underlying data storage type.  Presenting to the application this data in the desired format (string, int, float, etc) is trivial.

So, in conclusion, I don't see what you are offering.  If I develop a class called Foo, there would be additional work to develop an interface method so I could display its contents.  It would seem that your library would merely capitalize on this, without offering too much more (if anything).

It's late... maybe I have missed the boat... and everything you have explained.  Maybe I should talk to Greenspan.

---

### Post by worksofcraft on 2010-09-04
> **dwhitney67 said:**
> I guess I not in the market for that.

You "speak" just like Alan Greenspan; very sure of yourself, yet very vague.

... so what if you wanted to get some configuration data from a config file for your application and use a particular string from somewhere deep in that config file to identify the name of your log file?

The bit of the config file that you are interested in says something like:

```

USERLOG = %HOME$s/log # log file path using $HOME

```

Apart from reading and locating the USERLOG entry you would needed to substitute $HOME from the environment in one of strings.

```

 etc_item Etc("etc.etc"); // wrap the config file named etc.etc
 FILE *LogFile = fopen(env_item().form(Etc[i("USERLOG")]), "w");

```

See it is formatting my Linux environment wrapper env_item, with the format it locates and extracts from my configuration file etc.etc (implemented with my etc_item wrapper) and passing it straight on to open the file you want to write to.

Note: This is why this thread is called "Data Path". I thought just the name explains it enough :shock: Whatevah... if you think can write it easier without my library then don't be shy to show us how ;)

---

### Post by worksofcraft on 2010-09-05
Anyway... I'll upload a new .tar file on message 39 in a mo so everyone can see what I'm talking about.

Meanwhile I hate doing this but I have resorted to a macro :P to help aggregating items in containers on the fly

[php]
// This variadic macro really does simplify the syntax, but I don't like macros
#define CONTAIN(...) array_item( (item *[]) {__VA_ARGS__}, sizeof((item *[]) {__VA_ARGS__})/sizeof(item *))

// example packing two items to be used by the format:
cout << CONTAIN(&i(3), &dngettext_item("_ordinal")).gettext(
	"This is my %0$d%1/st$0$s format!"
) << endl;
[/php]

p.s. and for those who actually understood what I wuz talking about on the gettext issue...
test your understanding why does it give me this output...

"Translated my 3rd format!"

lol :popcorn:

---

### Post by slavik on 2010-09-05
> **Bachstelze said:**
> /usr vs. /usr/local depends on the OS.  Most (all?) Linux distributions put everything in /usr, but other systems like the BSDs that have a clear distinction between software in the base system and third-party software use /usr for the former and /usr/local for the latter.

When you compile something from source, or otherwise install it by another means than your OS's package manager, it's better to always put it in /usr/local unless you have a very good reason to.  /opt is good because you can get rid of the software with just a [font=monospace]sudo rm -rf /opt/foo[/font], but that's generally not needed (we have checkinstall and friends).
/opt is for software not following the *nix standards (mostly third party specialized apps).

creating a package to "copy" files is easy, see the sticky about creating simple deb packages, rpm is easy, too.

---

### Post by Bachstelze on 2010-09-05
> **slavik said:**
> /opt is for software not following the *nix standards (mostly third party specialized apps).

Mostly but not only. MacPorts on OS X uses it for example.

> creating a package to "copy" files is easy, see the sticky about creating simple deb packages, rpm is easy, too.

I know how to create a package, thank you very much. Just because I can, though, does not mean I always think I should. Sometimes I also don't want the package manager to know about something I "installed".

---

### Post by dwhitney67 on 2010-09-05
> **worksofcraft said:**
> ...

The bit of the config file that you are interested in says something like:

```

USERLOG = %HOME$s/log # log file path using $HOME

```

...

I'm still confused... why can't you keep things simple, such as merely specifying an entry (ie USERLOG) as:
```

USERLOG = $HOME/log

```
Anything that appears with a $ in front of it, up to a / or null character, will be considered an environment variable, which of course should be expanded, if possible.

---

### Post by worksofcraft on 2010-09-05
> **dwhitney67 said:**
> I'm still confused... why can't you keep things simple, such as merely specifying an entry (ie USERLOG) as:
```

USERLOG = $HOME/log

```
Anything that appears with a $ in front of it, up to a / or null character, will be considered an environment variable, which of course should be expanded, if possible.

That is indeed how one would code it in a shell script, but configuration file is not processed by shell script.

Instead I wrote a simple wrapper to parse it into a dictionary of many entries. From that I can select any I want by name.

After obtaining the desired entry one could then shell out to the shell interpreter to do the expanding. That only has access to the environment variables of the shell and also don't need or want the complexity of shell scripts to process my formats.

The format syntax I chose... I discussed this earlier: It's backward compatible with extended C++ formats which is backward compatable with original C formats. In this case a %s string format. Extended C++ format would alow a numeric identifier e.g. %5$s but I environent variables don't have numeric identifiers, so I extended that further to allow a name. In this case %HOME$s

anyway bed time... and I hope the earth quakes don't keep me awake again :(

---

### Post by dwhitney67 on 2010-09-05
Look at the code below, which works off of data similar to this:
```

# This is the path that should be used for creating the User's Log File.
USERLOG = $HOME/log

# This is merely another variable
OTHERVAR = foo

```

Code:
```

#include <fstream>
#include <map>
#include <string>
#include <vector>
#include <cstdlib>
#include <iostream>


std::vector<std::string>
tokenize(const std::string& str, const std::string& delim = " ")
{
   std::vector<std::string> tokens;

   std::string::size_type lastPos = str.find_first_not_of(delim, 0);
   std::string::size_type pos     = str.find_first_of(delim, lastPos);

   while (lastPos != std::string::npos || pos != std::string::npos)
   {
      tokens.push_back(str.substr(lastPos, pos - lastPos));

      lastPos = str.find_first_not_of(delim, pos);
      pos     = str.find_first_of(delim, lastPos);
   }

   return tokens;
}


class ConfigData
{
public:
   ConfigData() {}

   bool init(const char* configile);

   const char* get(const char* lookup) const;

private:
   typedef std::map<std::string, std::string> Data;

   Data myData;
};

bool
ConfigData::init(const char* configFile)
{
   using namespace std;

   bool    parseStatus = true;
   fstream file(configFile, ios::in);

   if (file)
   {
      string entry;

      while (getline(file, entry))
      {
         // skip comments and blank lines
         if (entry[0] == '#' || entry[0] == ' ' || entry.size() == 0) continue;

         vector<string> tokens = tokenize(entry, " =");

         if (tokens[1][0] == '$')  // data value is an environment var; must expand
         {
            const size_t slash  = tokens[1].find_first_of('/', 0);
            const string envStr = tokens[1].substr(1, slash - 1);
            const char*  envVar = getenv(envStr.c_str());

            if (envVar)
            {
               tokens[1] = envVar + tokens[1].substr(slash);
            }
            else
            {
               parseStatus = false;
               break;
            }
         }
 
         myData.insert(make_pair<string, string>(tokens[0], tokens[1]));
      }
   }
   else
   {
      parseStatus = false;
   }

   return parseStatus;
}


const char*
ConfigData::get(const char* lookup) const
{
   Data::const_iterator it = myData.find(lookup);

   if (it != myData.end())
   {
      return it->second.c_str();
   }

   return 0;
}


int main(int argc, char** argv)
{
   ConfigData cd;

   if (!cd.init(argv[1]))
   {
      std::cerr << "Failure to parse configuration file; exiting!" << std::endl;
      return -1;
   }

   std::cout << "USERLOG : " << cd.get("USERLOG")  << std::endl;
   std::cout << "OTHERVAR: " << cd.get("OTHERVAR") << std::endl;

   return 0;
}

```

P.S.  I've also attached the code/config file above as a tar-ball.

---

### Post by worksofcraft on 2010-09-05
That is very nicely written and highly functional configuration file parser you have written there. It also gives us exactly the syntax you wanted and expands all the environment variables as it processes each line :)

While I really like your use of STL templates, what it doesn't do is anything else: Like... what if you want to put in variables that **don't** come from the environment? Perhaps for instance, they are options that the user selects in a GUI, or specified in some other file or... even calculated somehow in your program.

Remember that my original objective was to extend *formatting capabilities* for use with internationalization because none of the libraries I looked at could do what I wanted. My aim has been to totally separate the data (under control of the programmer) and it's representation (in the hands of the translator).

Parsing config files and substituting variables has just been an incidental gratuitous application. So now I'm busy putting in utf-8 support and floating point parameters in my format stuff... oh well it's all good practice and my programming knowledge is gradually returning ;)

p.s. In any case that kind of concludes what we can do for setting paths to data files... so in closing, my apologies to anyone who was hoping to find an equivalent of the old MSDOS "Append" command for Linux here!

---

### Post by worksofcraft on 2010-09-06
Summary Package "ConForm"

Now available from:
[http://code.google.com/p/speaknumber/downloads/list](http://code.google.com/p/speaknumber/downloads/list)


Unaware of the implications for globalization most programmers still think that serializing objects to output streams is the right way to do it.

Yet things like Python and the Boost library have realized the need for more advanced formatting capabilities:

[http://www.boost.org/doc/libs/1_44_0/libs/format/index.html](http://www.boost.org/doc/libs/1_44_0/libs/format/index.html)

[http://www.python.org/dev/peps/pep-3101/](http://www.python.org/dev/peps/pep-3101/)

So this library goes beyond those... to the extent where, by way of example I can format an object that represents your environment settings with one that represents a configuration file, to get environment configured output strings.
Note: Unlike the afore mentioned, my facility remains backward compatible with the original C formatting semantics.

---

### Post by nvteighen on 2010-09-07
> **worksofcraft said:**
> Summary Package "ConForm"

Now available from:
[http://code.google.com/p/speaknumber/downloads/list](http://code.google.com/p/speaknumber/downloads/list)


Unaware of the implications for globalization most programmers still think that serializing objects to output streams is the right way to do it.

Yet things like Python and the Boost library have realized the need for more advanced formatting capabilities:

[http://www.boost.org/doc/libs/1_44_0/libs/format/index.html](http://www.boost.org/doc/libs/1_44_0/libs/format/index.html)

[http://www.python.org/dev/peps/pep-3101/](http://www.python.org/dev/peps/pep-3101/)

So this library goes beyond those... to the extent where, by way of example I can format an object that represents your environment settings with one that represents a configuration file, to get environment configured output strings.
Note: Unlike the afore mentioned, my facility remains backward compatible with the original C formatting semantics.

I haven't been able to review the code in detail, but I'll try... But just something: please set up the SVN repository, so you can work and push the code there and people can just branch the trunk code by using svn without having to download the tarball... Tarballs are usually used for releases, not development (and even though you consider your tarball as a release, you should still set SVN up and upload the code... it's just the way it works).

---

### Post by worksofcraft on 2010-09-07
> **nvteighen said:**
> I haven't been able to review the code in detail, but I'll try... But just something: please set up the SVN repository, so you can work and push the code there and people can just branch the trunk code by using svn without having to download the tarball... Tarballs are usually used for releases, not development (and even though you consider your tarball as a release, you should still set SVN up and upload the code... it's just the way it works).

Tyvm, all input is much appreciated :)

I don't yet know what SVN is and only learnt about code.google from that thread about tabs to spaces converter tool ([http://ubuntuforums.org/showthread.php?t=1560520](http://ubuntuforums.org/showthread.php?t=1560520)) You see the last OS I worked on was Windows 95 and all this Linux malarchy is kind of new to me :shock:

---

### Post by slavik on 2010-09-07
> **Bachstelze said:**
> ...
I know how to create a package, thank you very much. Just because I can, though, does not mean I always think I should. Sometimes I also don't want the package manager to know about something I "installed".

In what situation would you not want the package manager know about what you have installed? (this is why /opt/ is there, for software like this)

What happens when it starts overwriting your files because of a conflicting package?

As for the OSX Macports, it makes sense, since Macports is 3rd party and doesn't follow the OSX guidelines ($NAME.app in Applications directory). OSX itself doesn't follow the *nix conventions though.

---

### Post by nvteighen on 2010-09-07
> **worksofcraft said:**
> 
I don't yet know what SVN is and only learnt about code.google from that thread about tabs to spaces converter tool ([http://ubuntuforums.org/showthread.php?t=1560520](http://ubuntuforums.org/showthread.php?t=1560520)) You see the last OS I worked on was Windows 95 and all this Linux malarchy is kind of new to me :shock:

SVN is a version controlling system (for short, VCS): it makes you able to create revisions, merge them, etc. and that's really useful. A secondary feature, related but not primary, is the ability to set up somewhere to place your code and manage it from there.

Wikipedia phrases it better: [http://en.wikipedia.org/wiki/Apache_Subversion](http://en.wikipedia.org/wiki/Apache_Subversion)

I actually believe that Distributed VCSs (DVCS) are better. Canonical has set up a site called Launchpad ([https://launchpad.net/](https://launchpad.net/)) that uses the Bazaar system. Linus Torvalds has created another DVCS program called git. DVCS allows each user to have their own code branch, as opposed to tools like SVN that only allow for a central unique branch (and using permissions to regulate who can change the branch and who cannot).

---

### Post by worksofcraft on 2010-09-07
> **nvteighen said:**
> 
I actually believe that Distributed VCSs (DVCS) are better. Canonical has set up a site called Launchpad ([https://launchpad.net/](https://launchpad.net/)) that uses the Bazaar system. Linus Torvalds has created another DVCS program called git.

As it stands I'm quite happy to use a simple system and perhaps consider more advanced techniques when I've got to grips with the basics and I'm grateful to Google for providing free storage on the web. Actually I'm failing to fathom how to put my files into the SVN system in the first place :(

At the moment I'm just making things like file names a bit more consistent and putting it all in a namespace "conform", which is short for "container formatter".

My next concern is writing documentation. Currently there is only a.cc containing sets of tests that can be commented in or out and it's not really clear to the reader why any of it would be any use. :rolleyes:

Eventually I want to add proper css presentation to these html files, but I also want to get on and investigate Right to Left (R2L) languages... and things like formatting numbers in Arabic text with their kind of digits instead of ours.

---

### Post by nvteighen on 2010-09-07
I've read your code as much as I could and I've found several issues... but also something positive (I'll tell you at the end). I'll try to summarize it as best as possible to avoid a lengthy post.

It's mainly about knowing what tools are available to you. You use C++ but you keep using C, which makes you do some weird things like incrementing pointers to traverse a string, instead of using STL iterators and the like on a C++ string instance. 

Then, in item_print.cc you implement eat_num, an unsafe version of C's atol() (ASCII to long). It's actually worse than atol() because you happily assume you can return an unsigned long from a string, which you just can't. As soon as eat_num gets to the '-' character, the isdigit() check will fail for that character at the loop's first iteration and 0 will be returned. If unsigned longs are needed, implementing eat_num on atol() (or its C++ equivalent... I don't remember what it was) would have provided a safer procedure.

There are several cases, really... you kinda duplicate parts of strtok() in some places to tokenize strings, for example. Also, some stuff is already done by Glib, actually: UTF-8 and some extended printf() features like yours.

But possibly the worst is possibly your attempt of creating a generic-able class-hierarchy with "Item". It's completely unneeded: if this is about output, don't create types, just create stuff that take the already given types and interpret them correctly. It's just a display issue which you're working on, you're not trying to recreate NeXTStep/GNUStep's NSObject class for Objective-C!

What I really liked was proc_id.c. Ok, we discussed why it was a bit redundant, but I like the style and how the code is written... it's almost the opposite of the C++ modules. Ok, maybe the split_path function could be replaced by strtok, but the module is clean, nice and straightforward.

That's it... Keep working! I'm sure you'll get it right. :)

---

### Post by worksofcraft on 2010-09-07
> **nvteighen said:**
> 
... But possibly the worst is possibly your attempt of creating a generic-able class-hierarchy with "Item". It's completely unneeded: if this is about output, don't create types, just create stuff that take the already given types and interpret them correctly. It's just a display issue which you're working on, you're not trying to recreate NeXTStep/GNUStep's NSObject class for Objective-C!

...


Thanks for your insights and recommendations :)
p.s. Note: Because we seem to be getting way off the original topic I decided to make a new thread [http://ubuntuforums.org/showthread.php?p=9818291](http://ubuntuforums.org/showthread.php?p=9818291) about the problems I'm having with using standard libraries.

Originally my intention was to create an output formatting facility for STL containers so I DO indeed want to be using them more.

What I need though is for my "printf" equivalent to be able to reach into those containers and fetch the items identified by the format string. Not just into a container of basic  parameters, but recursively into potential containers within said containers.

I can't see any way of doing this other than having all my  containers derive from a common base class that has a virtual operator[] method for the format to call upon. :shock:

---

### Post by worksofcraft on 2010-09-12
As a follow up to this thread. I have included  comment in the source code of the package concerned. I would like to add an acknowledge of the code review contribution from nvteighen with his/her permission as I will be using it to make several adjustments to the code in the near future :)

```

/*
 * Conform: container string formatting routines
 *
 * This is original work by scaife dot chris at gmail dot com
 * (and e-mail harvesting spam bots begone!)
 *
 * This comment explains about the history of the code you now read.
 *
 * It was written in a very early form of C++ for an embedded 8 bit microprocessor
 * that had only a few kilo bytes of memory. There was no standard library and no
 * dynamic heap management capability (but we needed some kind of output routines).
 *
 * Later the code was ported to Java because that language lacked formatted output.
 * Alas, the Java community was unanimous: This was crap! Output should be done with
 * streams. Thus it lay dormant on a floppy disk in my garage for nearly 15 years.
 *
 * Then one day I decided to learn about Linux and discovered the gettext package.
 * Suddenly I realized the potential of what I had created all those years ago
 * so I ported it back to C++...
 *
 * Enjoy ;)
 *
 */

```

---

