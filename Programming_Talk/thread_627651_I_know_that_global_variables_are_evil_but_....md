---
title: "I know that global variables are evil but ..."
date: 2007-11-30
forum: Programming Talk
---

### Post by NeillHog on 2007-11-30
As the title says "I know that global variables are evil and those who use them should be publicly humiliated but ...."

I am writing a simple program with Python. It has a GUI made with Qt.

The main window (class theApp(GUI):) starts by reading the actual serial port from a configuration file.

It also has a menu point that when selected opens a "preferences" box (class prefDlg(frmPref):) 
This class begins by opening the configuration file and reading the current serial port. It adds this in to a lineEdit.

When the user closes the dialog, that calls a function in the class  prefDlg(frmPref): (def _acceptPreferences(self):) that writes the actual port back to the configuration file.

Up to now I don't have a huge problem but ..

The next time the user calls a function that uses the serial port I should ideally be using the one he just selected in the preferences dialog. 

This means I now need to open the configuration file at the start of every function

Or I could use a global value for the whole program containing the port. 

my problem is that both methods seem inelegant.
A global variable will put me in league with the devil.
Opening, reading and closing configuration files all over the place does not seem so good either.

As a configuration file is a fairly standard thing I hope there is a fantastic solution out there.

thanks for all any any help.
Neill

---

### Post by Wybiral on 2007-11-30
Can't you just wrap it in a class?

---

### Post by DuneSoldier on 2007-11-30
I'd use a Singleton to handle Configuration data that can be called from anywhere in the program.

```

//Java-ish code.
public class Configuration
{
     private static Configuration Config;

     private Configuration()
     {

     }

    public Configuration getInstance()
    {
        if(Config == null)
        {
           Config = new Configuration();
        }
     
        return Config;
    }
}

```

---

### Post by tyoc on 2007-11-30
In python there no exist the necesity to create a singleton, take a module (a .py) and write the code there, import it, thus "it will be like a singleton".
```

value = 5
 
if __name__ == "__nothing__":
   print "nothing!!!!"
else:
    print "or some... lol"
 
def Add1():
    global value
    value = value +1
def Dec1():
    global value
    value = value -1


Add1()
Add1()
Add1()
Dec1()
print value

```import it 1 time (or more times, doesnt matter, the impact will be 1 and only 1 instance of the module in the program... a "singleton").

---

### Post by pmasiar on 2007-11-30
for quick and dirty global object, make name of dictionary global. Read about keyword 'global'

---

### Post by Majorix on 2007-11-30
> **NeillHog said:**
> As the title says "I know that global variables are evil and those who use them should be publicly humiliated but ...."
Neill

That's wrong. You can do anything you want in your program. The "never use goto" and similar is just some annoyance.

---

### Post by Wybiral on 2007-11-30
> **Majorix said:**
> That's wrong. You can do anything you want in your program. The "never use goto" and similar is just some annoyance.

Well, yeah, you can write your entire program in obfuscated Perl if you want. But when it comes to best practice, there are certain design strategies that are considered taboo. And they got that way for a reason. Typically because they're either easy to abuse, or because they make maintainability a hassle. Unnecessary globals and gotos are among those things. The biggest issue with globals is the entire reason Python emphasizes on namespaces so much... Because they make namespace pollution hard to avoid (thus unmaintainable code).

---

### Post by LaRoza on 2007-11-30
> **Majorix said:**
> That's wrong. You can do anything you want in your program. The "never use goto" and similar is just some annoyance.

You can do anything you want, but should you, is the question.

I have programs that I wrote which use extensive use of globals and goto's, but they are in Fortran 77, in more modern languages, the use of these concepts are discouraged not because of irrational hate, but because of the lessons learned with earlier, less structured languages.

---

### Post by NeillHog on 2007-12-01
Thank you for the replies.
I need to do a lot more reading about "Singletons".

I understand from the above that reading a configuration file every time I need the serial port is not a problem but that the code I use to do it should be in one class which I call whenever I need a variable from the configuration file. As a suggestion:

Port = getConfVariable("port", "hardware") 

I could use the getConfVariable whenever I needed anything from my configuration file.

The question remains where to define the name of my configuration file? Here I can either hardcode it in to my getConfVariable class or I could use a global variable so that I can have it right at the top of my code where it is easy to find and easy to change if ever I want to change from ~/.gabow,conf

I appreciate all your helps and comments
Thanks!

---

### Post by winch on 2007-12-01
> **NeillHog said:**
> I understand from the above that reading a configuration file every time I need the serial port is not a problem but that the code I use to do it should be in one class which I call whenever I need a variable from the configuration file.

Why read the config file multiple times when you can just store the value in the config object?

> The question remains where to define the name of my configuration file? Here I can either hardcode it in to my getConfVariable class or I could use a global variable so that I can have it right at the top of my code where it is easy to find and easy to change if ever I want to change from ~/.gabow,conf

Sure if you only have one item at the top of your code it is easy to find. What if you have 10 items? or 50 items?

---

### Post by pmasiar on 2007-12-01
> **NeillHog said:**
> The question remains where to define the name of my configuration file? Here I can either hardcode it in to my getConfVariable class or I could use a global variable so that I can have it right at the top of my code where it is easy to find and easy to change if ever I want to change from ~/.gabow,conf


Having name of config file as a global is fine. But you use it only once, to populate the "config" global object, right?

Some more complicated systems may have "trigger file" to allow for multiple config files: if present, use "developer" version. If absent, use "production" (which reports error to log file and not to the user).

> I am a newbie. I have been for many years now. Sometimes I feel that I understand things, turn the corner and find that there is even more to understand. 

I really like your sig. With this attitude, nothing can stop you from learning!

---

### Post by NeillHog on 2007-12-01
pmasiar wrote
> Why read the config file multiple times when you can just store the value in the config object?

Thank you for that suggestion.
Excuse me being a bit slow but would the object not then need to be global if I want to use the values in a variety of functions and classes?

Or am I missing something very important here?

At the moment I start by reading the conFigFile
```
config = ConfigParser.ConfigParser()
config.read(configFile)
```
and obviously once I have done that I have everything in config. 

But I am using the config file to know which directory to open in a fileDialog in a different function, for setting the serial port in a Preference Dialog (different class), and and ...

So I will need to pass config to every class if it is not global. Is this really the sensible thing to do?

Thank you for helping me understand all this.
Neill

---

### Post by winch on 2007-12-01
> **NeillHog said:**
> Excuse me being a bit slow but would the object not then need to be global if I want to use the values in a variety of functions and classes?

You would need a mechanism so parts of the code that need the configuration values can access them.

Making the config object global is one way of doing it.

The previously mentioned [Singleton]("http://en.wikipedia.org/wiki/Singleton_pattern") pattern can be used in a way similar to a global. IMO used in this way you might as well just use the simpler approach of a global.

I don't think small programs with a couple of globals are bad per say. You can keep track of the globals and where they are used and hopefully spot all the cases a global is a bad choice.

Alternatively you could pass the config object to any objects that need it via their constructor. Or pass config values to methods that need them. These methods avoid the problems using a global/singleton.

---

### Post by NeillHog on 2007-12-02
Thank you all.

To summarize -
There are three ways I can deal with my config file.
1. Use a singleton (still have not understood this fully).
2. Use a global, either for the config file or the config object.
3. Pass the file name or the config object  to each function that needs it.

I have looked at my program and there are numerous places where I write to the config file:
1. leaving the preferences window.
2. leaving the file select dialog (last file and last directory selected).
3. After pressing start (user input)
In all these places I need to write to the file. Or I could write to the object and then write the file on program exit.

I think I will try having the object as a global, reading it at the start, writing it to file at the end. The file name will have to be explicitly defined in the reading and writing functions.

Thanks

---

### Post by pmasiar on 2007-12-02
> **NeillHog said:**
> 
1. Use a singleton (still have not understood this fully).

Pretty good reason NOT to use it, and just use global config object instead :-)

> 
I have looked at my program and there are numerous places where I write to the config file:


You should extract all this code into one module, and call its routines.

It does not have to be OO code, modules are fine:

have config.py module, with data = {}. You can access it (after importing) in other modules: 

[php]
config.read() # reads config from outside config.txt file (into config.data dict)
config.update_pref(key, val) # changes value
dbase = config.data['dbase'] # access value
config.save_prefs() # save prefs, handles the details 
# possibly overwriting orig config.txt file, making backup etc
[/php]


No OOP, no problems. :-)
This is why I like Python.

Or, if your need will grow beyond this simple hack, you can use ConfigParser in core library

Edit: BTW please note that config in my solution is not a global, but a module.

---

### Post by xtacocorex on 2007-12-02
I wouldn't say that all global variables are bad, in certain circumstances, they can be handy.  In all my FORTRAN programs I make filenames and PI global variables just so they can be referenced from all my subroutines/functions.  I digress...

As for your problem, I'd stick with the global config object and write to it on close, but also write to it every so often during execution just to make sure any changes to the config don't get lost in a program crash.

---

### Post by NeillHog on 2007-12-03
Ok! Thanks for all the help. Now that I more or less understand what I am doing I will go away and solve the problem - probably with a global config object.
Thanks!

---

