---
title: "[Python] Revamping a game, need help"
date: 2008-11-28
forum: Programming Talk
---

### Post by dodle on 2008-11-28
I hope that I haven't had this problem resolved before, and I apologize if this is repetitive, but I can't get this script to work.  The problem that I am having is described in the #comments.[PHP]#Trial of Aolis Simple Version 0.1a

x = 0
y = 0

# The following functions should add or subtract x and y
def button_n(x):
    x = x+1
    return x

def button_s(x):
    x = x-1
    return x

def button_e(y):
    y = y+1
    return y

def button_w(y):
    y = y-1
    return y

def opening():
    print "This is the opening"

loop_master = True
while loop_master == True:
    opening()
    loop_slave = True
    while loop_slave == True:
        command = raw_input("\nCOMMAND\n: ").lower().split()
        if len(command) < 1:
            print "\nPlease enter a command."
        elif len(command) == 1:
            # here is where the functions are executed but x y always prints 0 0 no matter what
            if command[0] in ('n', 'north', 'u', 'up'):
                button_n(x)
            elif command[0] in ('s', 'south', 'd', 'down'):
                button_s(x)
            elif command[0] in ('e', 'east', 'r', 'right'):
                button_e(y)
            elif command[0] in ('w', 'west', 'l', 'left'):
                button_w(y)
            else:
                loop_slave = False
        print "\n%s %s" % (x, y)  # x y is always 0 0

raw_input("\nPress \"enter\" to exit.")[/PHP]
Edit: Fixed errors in script where len() needed.

---

### Post by tiachopvutru on 2008-11-29
You forgot to assign the values your functions return back to x or y...

---

### Post by dodle on 2008-11-29
I don't understand.  I thought that "x = x + 1" assigned the value to return.

---

### Post by Tony Flury on 2008-11-29
where you do :
```

def button_n(x):
    x=x+1
    return x

```
in a function, it is creating and then changing the local value of x inside the function only. The fact that you return the value of x from the function is irrelevant because your main code is not using that return value, and once outside function you no longer have access to the value of x inside the function, and of course x and y both are zero outside the function.

try this - and similar in the right places in your code : 
```

x = button_n(x)

```

what this is doing is using the return value from the function as the new value of x - your code will then do what you expect.

---

### Post by dodle on 2008-11-29
Thank you, that works perfectly.

---

### Post by Greyed on 2008-11-29
The alternative, of course, is to not pass the variables.  But name spaces are good so stick with that.

If you don't mind me offering a few more suggestions (*cough* constructive criticisms *cough*)

You've got some state assignments and checks for the while loops. Barring the talk about while 1: break I actually wanted to point out that your check is a tad off.

[php]
loop_master = True
while loop_master == True:
    opening()
    loop_slave = True
    while loop_slave == True:
[/php]What you're doing in those while checks is checking the boolean value (True/False) of the statement.  So when doing check of, for example, x > 10, we're really checking to see if that statement is True or False.  What you're doing above is checking to see if True is True.  IE, loop_master and loop_slave are boolean values.  The statement itself returns a boolean value.  So instead of checking to see if the variable is the same as True, just check to see if it *is* True.  EG:

[php]
 loop_master = True
 while loop_master:
     opening()
     loop_slave = True
     while loop_slave:
[/php]    If loop_master and loop_slave are True then the while loops will proceed.  If they're False, they'll exit.  On simple statements like this it doesn't make a huge visual difference.  However on compound statements it makes a world of difference.  Compare the following two ifs.

[php]
if blank == False and not color == '':
if not blank and color:
[/php]The other suggestion is for command parsers, go with dicts.  You have a large chain of elifs.  4-5 aren't a problem but a dozen or so would.  Compare this...

[php]
            if command[0] in ('n', 'north', 'u', 'up'):
                button_n(x)
            elif command[0] in ('s', 'south', 'd', 'down'):
                button_s(x)
            elif command[0] in ('e', 'east', 'r', 'right'):
                button_e(y)
            elif command[0] in ('w', 'west', 'l', 'left'):
                button_w(y)
            else:
                loop_slave = False
[/php]...to this...

[php]
# this would be above the loops
commands = { 'n' : button_n, 'north' : button_n, 'u' : button_n, 'up' : button_n,
             's' : button_s, 'south' : button_s, 'd' : button_s, 'down' : button_s,
             'e' : button_e, 'east' : button_e, 'r' : button_e, 'right' : button_e,
             'w' : button_w, 'west' : button_w, 'l' : button_w, 'left' : button_w,
}

# this would replace the elif chain:
if command[0].lower() in commands.keys():
    commands[command]()
else:
    loop_slave = False
[/php]It looks more convoluted, and admittedly, it is.  But to add additional commands you don't need to change the command check at all.  You just add them to the commands dict.  

[php]
# this would be above the loops
commands = { 'n' : button_n, 'north' : button_n, 'u' : button_n, 'up' : button_n,
             's' : button_s, 'south' : button_s, 'd' : button_s, 'down' : button_s,
             'e' : button_e, 'east' : button_e, 'r' : button_e, 'right' : button_e,
             'w' : button_w, 'west' : button_w, 'l' : button_w, 'left' : button_w,
             'i' : inventory, 'inv' : inventory, 'inventory' : inventory,
             'eq' : equip, 'equip' : equip
             'se' : search, 'search' : search      
}
[/php]Notice that for each additional action only a single line is added as opposed to one line for the check and one line for the command.  Also unlike an elif chain the lookup time for each command does not vary nor does it get longer with each additional item you add.  On the flip side you'll note I'm not passing variables to the function nor would I use any return.  It changes the variable handing to presume the functions are accessing the variables outside their scope be it global or, better, inside some class/library name space both reside.

---

### Post by wmcbrine on 2008-11-29
An alternative way to implement this, *which I do not recommend*, if you wanted to treat these (to use Pascal terminology) more as procedures than functions, would be:

```

def button_n():
    global x
    x = x+1

```

However, unless these functions are just meant as placeholders for potentially more elaborate implementations to come, my real recommendation is to drop them altogether and just put "x = x + 1", etc. inline. (Or, preferably, "x += 1".)

---

### Post by dodle on 2008-11-29
Thanks Greyed, that is very helpful.  I am going to try and use that in my code right now.  I'm going to leave this thread unsolved for now... at least until I post my new code.

---

### Post by dodle on 2008-11-29
Here is the script that I was working on, and below it I've tried to implement Greyed's dictionary but am having troubles.  I know that I'm not doing something right but I'm not sure what.

Without any dictionaries:[PHP]# Game Template 0.1.1a

x = 0  # Represents where the character is standing on a horizontal plane
y = 0  # Represents where the character is standing on a vertical plane

pack = []  # Represents items currently in possession
task = []  # Special list to initiate or prevent initiation of events

loc = None
cur_item = None

# Determines which direction the character moves according to user input
def button_n(y):
    y = y + 1
    print "\nYou move one space to the north."
    return y

def button_s(y):
    y = y - 1
    print "\nYou move one space to the south."
    return y

def button_e(x):
    x = x + 1
    print "\nYou move one space to the east."
    return x

def button_w(x):
    x = x - 1
    print "\nYou move one space to the west."
    return x

def location(x, y, loc):
    """Determines the "name" of the current location which
    is used to find the correct description."""
    if x == 0 and y == 0:
        loc = "forest"
    elif x == 0 and y == 1:
        loc = "forest n"
    elif -1 <= x <= 1 and y == 2:
        loc = "mount"
    return loc

def descr(loc):
    """A description of the current area reflected by the
    the variables x and y."""
    if loc == "forest":
        print "You are in the forest."
    elif loc == "forest n":
        print "You are in the north forest."
    elif loc == "mount":
        print "Your are near the mountains."

def event():
    pass

def add_pack(pack, cur_item):
    pack.append(cur_item)
    return pack

def quit_game(loop_slave):
    confirm = raw_input("\nAre you sure you want to quit?  \"yes\" to confirm.\n: ").lower()
    if confirm in ('y', 'yes'):
        loop_slave = False
    return loop_slave

def replay(loop_master):
    """Decides wether the game will be exited or played over."""
    loop_replay = True
    while loop_replay == True:
        command = raw_input("\nWould you like to play again? y/n\n: ").lower()
        if command in ('n', 'no'):
            loop_master = False
            loop_replay = False
        elif command in ('y', 'yes'):
            loop_replay = False
        else:
            print "\n\"yes\" or \"no\"?"
    return loop_master


# Game Loop
loop_master = True
while loop_master == True:
    loop_slave = True
    while loop_slave == True:
        command = raw_input("\nCOMMAND\n: ").lower().split()
        
        # Response if user does not input anything
        if len(command) < 1:
            print "\nPlease enter a command."
        
        # For user input of only one word
        elif len(command) == 1:
            if command[0] in ('n', 'north'):
                y = button_n(y)
            elif command[0] in ('s', 'south'):
                y = button_s(y)
            elif command[0] in ('e', 'east'):
                x = button_e(x)
            elif command[0] in ('w', 'west'):
                x = button_w(x)
            elif command[0] in ('ne', 'northeast'):
                y = button_n(y)
                x = button_e(x)
            elif command[0] in ('nw', 'northwest'):
                y = button_n(y)
                x = button_w(x)
            elif command[0] in ('se', 'southeast'):
                y = button_s(y)
                x = button_e(x)
            elif command[0] in ('sw', 'wouthwest'):
                y = button_s(y)
                x = button_w(x)

            elif command[0] in ('exit', 'quit'):  # To quit the game
                loop_slave = quit_game(loop_slave)

            else:
                print "\n\"%s\" is not understood." % (command[0])

            loc = location(x, y, loc)  # Compares current location against x y
            print loc
            descr(loc)  # Displays a definition of location
        
        # For user input of two words
        elif len(command) == 2:
            if command[0] in ('take', 'get', 'acquire', 'retrieve'):
                pass
            elif command[0] in ('search', 'look', 'investigate', 'examine'):
                pass
            elif command[0] in ('buy', 'purchase', 'trade'):
                pass
            elif command[0] in ('light', 'ignite', 'burn'):
                pass
            else:
                print "\n\"%s\" is not understood." % (command[:])
        # For user input of more than two words
        elif len(command) > 2:
            print "\"%s\" is not recognized." % (command)
        print "%s %s" % (x, y)
        
    # Decides whether the game will be exited or played over
    loop_master = replay(loop_master)

raw_input("\nPress \"enter\" to exit.\n")[/PHP]Replaced some "elifs" with dictionary:[PHP]# Game Template 0.1.2a

x = 0  # Represents where the character is standing on a horizontal plane
y = 0  # Represents where the character is standing on a vertical plane

pack = []  # Represents items currently in possession
task = []  # Special list to initiate or prevent initiation of events

loc = None
cur_item = None

# Determines which direction the character moves according to user input
def button_n(y):
    y = y + 1
    print "\nYou move one space to the north."
    return y

def button_s(y):
    y = y - 1
    print "\nYou move one space to the south."
    return y

def button_e(x):
    x = x + 1
    print "\nYou move one space to the east."
    return x

def button_w(x):
    x = x - 1
    print "\nYou move one space to the west."
    return x

def location(x, y, loc):
    """Determines the "name" of the current location which
    is used to find the correct description."""
    if x == 0 and y == 0:
        loc = "forest"
    elif x == 0 and y == 1:
        loc = "forest n"
    elif -1 <= x <= 1 and y == 2:
        loc = "mount"
    return loc

def descr(loc):
    """A description of the current area reflected by the
    the variables x and y."""
    if loc == "forest":
        print "You are in the forest."
    elif loc == "forest n":
        print "You are in the north forest."
    elif loc == "mount":
        print "Your are near the mountains."

def event():
    pass

def add_pack(pack, cur_item):
    pack.append(cur_item)
    return pack

def quit_game(loop_slave):
    confirm = raw_input("\nAre you sure you want to quit?  \"yes\" to confirm.\n: ").lower()
    if confirm in ('y', 'yes'):
        loop_slave = False
    return loop_slave

def replay(loop_master):
    """Decides wether the game will be exited or played over."""
    loop_replay = True
    while loop_replay == True:
        command = raw_input("\nWould you like to play again? y/n\n: ").lower()
        if command in ('n', 'no'):
            loop_master = False
            loop_replay = False
        elif command in ('y', 'yes'):
            loop_replay = False
        else:
            print "\n\"yes\" or \"no\"?"
    return loop_master

commands = {'n' : button_n, 'north' : button_n, 's' : button_s, 'south' : button_s,
            'e' : button_e, 'east' : button_e, 'w' : button_w, 'west' : button_w}



# Game Loop
loop_master = True
while loop_master:
    loop_slave = True
    while loop_slave:
        command = raw_input("\nCOMMAND\n: ").lower().split()
        
        # Response if user does not input anything
        if len(command) < 1:
            print "\nPlease enter a command."
        
        # For user input of only one word
        elif len(command) == 1:
            if command in commands.keys():
                commands[command]()
            elif command[0] in ('exit', 'quit'):  # To quit the game
                loop_slave = quit_game(loop_slave)

            else:
                print "\n\"%s\" is not understood." % (command[0])

            loc = location(x, y, loc)  # Compares current location against x y
            print loc
            descr(loc)  # Displays a definition of location
        
        # For user input of two words
        elif len(command) == 2:
            if command[0] in ('take', 'get', 'acquire', 'retrieve'):
                pass
            elif command[0] in ('search', 'look', 'investigate', 'examine'):
                pass
            elif command[0] in ('buy', 'purchase', 'trade'):
                pass
            elif command[0] in ('light', 'ignite', 'burn'):
                pass
            else:
                print "\n\"%s\" is not understood." % (command[:])
        # For user input of more than two words
        elif len(command) > 2:
            print "\"%s\" is not recognized." % (command)
        print "%s %s" % (x, y)
        
    # Decides whether the game will be exited or played over
    loop_master = replay(loop_master)

raw_input("\nPress \"enter\" to exit.\n")[/PHP]This one dictionary has lightened my script by .54 kb:).  The way I had this game written before it was 106 kb.  I should be able to reduce that by more than half now.  Thanks again everyone.

I'm going to go to sleep now, so I probably won't respond for a while.

---

### Post by nvteighen on 2008-11-29
> **Greyed said:**
> 

[php]
# this would be above the loops
commands = { 'n' : button_n, 'north' : button_n, 'u' : button_n, 'up' : button_n,
             's' : button_s, 'south' : button_s, 'd' : button_s, 'down' : button_s,
             'e' : button_e, 'east' : button_e, 'r' : button_e, 'right' : button_e,
             'w' : button_w, 'west' : button_w, 'l' : button_w, 'left' : button_w,
}

# this would replace the elif chain:
if command[0].lower() in commands.keys():
    commands[command]()
else:
    loop_slave = False
[/php]It looks more convoluted, and admittedly, it is.  But to add additional commands you don't need to change the command check at all.  You just add them to the commands dict.  

[php]
# this would be above the loops
commands = { 'n' : button_n, 'north' : button_n, 'u' : button_n, 'up' : button_n,
             's' : button_s, 'south' : button_s, 'd' : button_s, 'down' : button_s,
             'e' : button_e, 'east' : button_e, 'r' : button_e, 'right' : button_e,
             'w' : button_w, 'west' : button_w, 'l' : button_w, 'left' : button_w,
             'i' : inventory, 'inv' : inventory, 'inventory' : inventory,
             'eq' : equip, 'equip' : equip
             'se' : search, 'search' : search      
}
[/php]

Really impressive simple and great solution. I'll keep this in mind for the future. Thanks!

---

### Post by dodle on 2008-11-29
[PHP]hello = "hello"
commands = { "n" : hello
}


command = raw_input("What would you like to do?\n: ").lower().split()
# this would replace the elif chain:
if command[0] in commands.keys():
    commands[command]()
else:
    print "That's not \"n\"."[/PHP]I'm getting the following error: 
in <module>
    commands[command]()
TypeError: unhashable type: 'list'

---

### Post by tiachopvutru on 2008-11-29
There are two errors in that one. The first one is reported to you. You can reproduce in by passing a list as a key for dictionary.
*command* is a list, and it looks like you want to pass in *command[0]* instead.

For the second error: *hello* is not a function.

---

### Post by dodle on 2008-12-04
I finally figured out how to use one of the GUI toolkits, so I am very happy.  I've got a script that I'm writing for my game with wxWidgets (err wxPython, whatever it is called), but was wondering if I could get a little help.  It's still pretty far from being complete.  What I want to do is display the coordinates when the "North", "South", "East", or "West" buttons are pushed.  The coordinates of the main character are going to be represented by x and y.  Right now all that prints out is the text defined in the methods.  I hope I am being clear.  Here is my script:[PHP]import wx

MenuItem_exit = 101
MenuItem_about = 100

class MainWindow(wx.Frame):
    def __init__(self, parent, ID, title):
        wx.Frame.__init__(self, parent, ID, title,
                        wx.DefaultPosition, wx.Size(800, 600),
                        wx.DEFAULT_FRAME_STYLE & ~ (wx.RESIZE_BORDER |
                        wx.RESIZE_BOX | wx.MAXIMIZE_BOX))
        
        # ------ Dialogue when "X" is pressed
        self.Bind(wx.EVT_CLOSE, self.QuitGame)

        # ------ Create the Status Bar
        self.CreateStatusBar()
        self.SetStatusText("Active")
        
        #self.FirePic = wx.Bitmap('display/fire.bmp')
        #wx.EVT_PAINT(self, self.ShowBack)

        # ------ Define some colors for background
        white = wx.Colour(255, 255, 255)
        black = wx.Colour(0, 0, 0)
        red = wx.Colour(255, 0, 0)
        green = wx.Colour(0, 255, 0)
        blue = wx.Colour(0, 0, 255)
        yellow = wx.Colour(255, 255, 0)
        dblue = wx.Colour(0,0,162)
        mygreen = wx.Colour(10,133,2)
        
        # ------ Menu Items
        file = wx.Menu()
        help = wx.Menu()
        
        # ------ Variables to symbolize the current area
        x = 0
        y = 0
        self.pos = wx.TextDataObject("Current Position is: %s %s" % (x,y))
        
        # ------ Display area for text output
        screen = wx.TextCtrl(self, 1,
                            style=wx.TE_MULTILINE|wx.BORDER_SUNKEN|wx.TE_READONLY|
                            wx.TE_RICH2,
                            size =(793, 349))
        font = wx.Font(14, wx.ROMAN, wx.NORMAL, wx.NORMAL)
        screen.SetStyle(44, 44, wx.TextAttr("#FFFFFF",wx.NullColour, font))
        screen.SetBackgroundColour(black)
        #wx.EVT_PAINT(screen, self.ShowBack)
        self.scr = screen
        self.scr.WriteText("Trial of Aolis\n")

        # ------ Area for controls
        controls = wx.Panel(self, -1, (0, 350), (800, 250))
        
        # ------ Directional Buttons
        north = wx.Button(controls, -1, "North", (365,5), (40,40))
        south = wx.Button(controls, -1, "South", (365,55), (40,40))
        east = wx.Button(controls, -1, "East", (415,30), (40,40))
        west = wx.Button(controls, -1, "West", (315,30), (40,40))
        pack = wx.Button(controls, -1, "Check Pack", (0, 120))
        search = wx.Button(controls, -1, "Search Area", (100,120))
        take = wx.Button(controls, -1, "Take Item", (200, 120))
        
        # ------ Number Buttons
        one1 = wx.Button(controls, -1, "1", (500, 5), (20, 20))
        one2 = wx.Button(controls, -1, "2", (525, 5), (20, 20))
        one3 = wx.Button(controls, -1, "3", (550, 5), (20, 20))
        one4 = wx.Button(controls, -1, "4", (575, 5), (20, 20))

        # ------ Pack Items Controls
        packstr = "Pack Contents"
        text = wx.StaticText(controls, -1, packstr, (5, 0))
        font = wx.Font(15, wx.NORMAL, wx.NORMAL, wx.NORMAL)
        text.SetFont(font)
        wx.StaticText(controls, -1, "Item 1", (5, 35))
        wx.StaticText(controls, -1, "Item 2", (5, 50))
        wx.StaticText(controls, -1, "Item 3", (5, 65))
        wx.StaticText(controls, -1, "Item 4", (5, 80))
        wx.StaticText(controls, -1, "Item 5", (5, 95))
        

        # ------ Menu Dropdown Items
        file.Append(MenuItem_exit, "E&xit", "Quit the game?")
        help.Append(MenuItem_about, "&About", "About the game")
        
        # ------ Create the Menu Bar
        MenuBar = wx.MenuBar()
        MenuBar.Append(file, "&File")
        MenuBar.Append(help, "&Help")
        self.SetMenuBar(MenuBar)

        # ------ Menu Events when a menu item is selected
        wx.EVT_MENU(self, MenuItem_exit, self.QuitGame)
        wx.EVT_MENU(self, MenuItem_about, self.AboutGame)
        
        # ------ Events for when directionl buttons are pressed
        north.Bind(wx.EVT_BUTTON, self.N_Press)
        south.Bind(wx.EVT_BUTTON, self.S_Press)
        east.Bind(wx.EVT_BUTTON, self.E_Press)
        west.Bind(wx.EVT_BUTTON, self.W_Press)
        
        self.Centre()

    def N_Press(self, event):
        font = wx.Font(12, wx.ROMAN, wx.NORMAL, wx.NORMAL)
        self.scr.SetStyle(-1, -1, wx.TextAttr("#FFFFFF",wx.NullColour, font))        
        self.scr.WriteText("North\n")

    def S_Press(self, event):
        font = wx.Font(12, wx.ROMAN, wx.NORMAL, wx.NORMAL)
        self.scr.SetStyle(-1, -1, wx.TextAttr("#FFFFFF",wx.NullColour, font))        
        self.scr.WriteText("South\n")
    
    def E_Press(self, event):
        font = wx.Font(12, wx.ROMAN, wx.NORMAL, wx.NORMAL)
        self.scr.SetStyle(-1, -1, wx.TextAttr("#FFFFFF",wx.NullColour, font))        
        self.scr.WriteText("East\n")
    
    def W_Press(self, event):
        font = wx.Font(12, wx.ROMAN, wx.NORMAL, wx.NORMAL)
        self.scr.SetStyle(-1, -1, wx.TextAttr("#FFFFFF",wx.NullColour, font))        
        self.scr.WriteText("West\n")
            
    def QuitGame(self, event):
        dlg = wx.MessageDialog(self, 
            "Do you really want to quit? All information will be lost.",
            "Confirm Quit", wx.OK|wx.CANCEL|wx.ICON_QUESTION)
        result = dlg.ShowModal()
        dlg.Destroy()
        if result == wx.ID_OK:
            self.Destroy()
    
    def ShowBack(self,event):
        bg = wx.PaintDC(self)
        bg.DrawBitmap(self.FirePic, 0, 0)
    
    def AboutGame(self, event):
        about_text = "Trial of Aolis WX"
        dlg = wx.MessageDialog(self, "\
Trial of Aolis WX v0.0.1\n\n\
Created by Deluge 2008",
                                about_text, wx.OK)
        dlg.ShowModal()
    

class AolisGame(wx.App):
    def OnInit(self):
        frame = MainWindow(None, -1, "Trial of Aolis WX v0.0.1")
        frame.Show(True)
        self.SetTopWindow(frame)
        return(True)

app = AolisGame(0)
app.MainLoop()[/PHP]

---

