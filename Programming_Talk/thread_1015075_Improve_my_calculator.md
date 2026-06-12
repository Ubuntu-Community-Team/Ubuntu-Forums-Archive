---
title: "Improve my calculator"
date: 2008-12-18
forum: Programming Talk
---

### Post by dodle on 2008-12-18
If anybody would like to help me improve my script I would really appreciate it.  Remember, I'm a novice.

Written in Python & wxPython:[PHP]#!/usr/share/env python

# wxCalculator v0.0.0.2

import wx

ID_Exit = 100

ID_About = 200

class MainWindow(wx.Frame):
    def __init__(self, parent, ID, title):
        wx.Frame.__init__(self, parent, ID, title,
                            wx.DefaultPosition, (300,400),
                            wx.DEFAULT_FRAME_STYLE & ~(wx.RESIZE_BORDER|
                            wx.RESIZE_BOX|wx.MAXIMIZE_BOX))
        
        

        # ------ Giving the window an icon
        _icon = wx.EmptyIcon()
        _icon.CopyFromBitmap(wx.Bitmap("data/icon16.ico", wx.BITMAP_TYPE_ANY))
        self.SetIcon(_icon)

        # ------ Setting up the Menu and Status bars
        Cmenubar = wx.MenuBar()
        file = wx.Menu()
        help = wx.Menu()
        file.Append(ID_Exit, "E&xit", "Quit wxCalculator")
        help.Append(ID_About, "&About", "About wxCalculator")
        Cmenubar.Append(file, "&File")
        Cmenubar.Append(help, "&Help")
        self.SetMenuBar(Cmenubar)
        self.CreateStatusBar()
        self.SetStatusText(" 0.0.0.2")
        
        wx.EVT_MENU(self, ID_Exit, self.Cclose)
        wx.EVT_MENU(self, ID_About, self.Cabout)

        
        # ------ Setting font for the output
        CFont = wx.Font(14, wx.MODERN, wx.NORMAL, wx.FONTWEIGHT_BOLD)
        CFont2 = wx.Font(12, wx.MODERN, wx.NORMAL, wx.FONTWEIGHT_BOLD)
        
        
        # ------ Setting up the panels
        self.Panel1 = wx.Panel(self, -1, (0,0), size=(300,35))
        self.COutput = wx.TextCtrl(self.Panel1, -1, pos=(22,5), size=(250,30),
                                    style=wx.ALIGN_RIGHT|wx.TE_PROCESS_ENTER|
                                    wx.TE_READONLY)
        self.COutput.SetFont(CFont)
        self.COutput.SetFocus()
        
        self.Panel2 = wx.Panel(self, -1, (0,35), (300,379))
        self.Panel2.SetFont(CFont2)
        
        ###### MEMORY BUTTONS ######
        self.clear_mem = wx.Button(self.Panel2, -1, "CLR\nM", (5,60), (50,40))
        self.set_mem = wx.Button(self.Panel2, -1, "SET\nM", (5,105), (50,40))
        self.read_mem = wx.Button(self.Panel2, -1, "READ\nM", (5,150), (50,40))
        
        self.CMem = []  # For storing Calculator input
        self.MMem = ""  # For storing from Memory Buttons
        
        self.clear_mem.Bind(wx.EVT_BUTTON, self.CClrM)
        self.set_mem.Bind(wx.EVT_BUTTON, self.CSetM)
        self.read_mem.Bind(wx.EVT_BUTTON, self.CReadM)
        
        ###### Clear Buttons ######
        
        self.backspace = wx.Button(self.Panel2, -1, "BKSPC", (70,15), (70,40))
        self.clrCE = wx.Button(self.Panel2, -1, "CE", (145,15), (70,40))
        self.clrC = wx.Button(self.Panel2, -1, "C", (220,15), (70,40))
        
        self.backspace.Bind(wx.EVT_BUTTON, self.BackSPC)
        self.clrCE.Bind(wx.EVT_BUTTON, self.ClearCE)
        self.clrC.Bind(wx.EVT_BUTTON, self.ClearC)
        
        ###### Numerical Buttons ######
        
        self.seven = wx.Button(self.Panel2, -1, "7", (70,60), (50,40))
        self.four = wx.Button(self.Panel2, -1, "4", (70,105), (50,40))
        self.one = wx.Button(self.Panel2, -1, "1", (70,150), (50,40))
        self.zero = wx.Button(self.Panel2, -1, "0", (70,195), (50,40))
        self.eight = wx.Button(self.Panel2, -1, "8", (125,60), (50,40))
        self.five = wx.Button(self.Panel2, -1, "5", (125,105), (50,40))
        self.two = wx.Button(self.Panel2, -1, "2", (125,150), (50,40))
        self.nine = wx.Button(self.Panel2, -1, "9", (180,60), (50,40))
        self.six = wx.Button(self.Panel2, -1, "6", (180,105), (50,40))
        self.three = wx.Button(self.Panel2, -1, "3", (180,150), (50,40))
        
        self.seven.Bind(wx.EVT_BUTTON, self.press7)
        self.four.Bind(wx.EVT_BUTTON, self.press4)
        self.one.Bind(wx.EVT_BUTTON, self.press1)
        self.zero.Bind(wx.EVT_BUTTON, self.press0)
        self.eight.Bind(wx.EVT_BUTTON, self.press8)
        self.five.Bind(wx.EVT_BUTTON, self.press5)
        self.two.Bind(wx.EVT_BUTTON, self.press2)
        self.nine.Bind(wx.EVT_BUTTON, self.press9)
        self.six.Bind(wx.EVT_BUTTON, self.press6)
        self.three.Bind(wx.EVT_BUTTON, self.press3)
        
        
        ###### Equation Buttons ######
        
        self.Div = wx.Button(self.Panel2, -1, "/", (240,60), (50,40))
        self.Mul = wx.Button(self.Panel2, -1, "x", (240,105), (50,40))
        self.Sub = wx.Button(self.Panel2, -1, "-", (240,150), (50,40))
        self.Add = wx.Button(self.Panel2, -1, "+", (240,195), (50,40))
        self.Equ = wx.Button(self.Panel2, -1, "=", (240,240), (50,40))
        
        self.Div.Bind(wx.EVT_BUTTON, self.numDiv)
        self.Mul.Bind(wx.EVT_BUTTON, self.numMul)
        self.Sub.Bind(wx.EVT_BUTTON, self.numSub)
        self.Add.Bind(wx.EVT_BUTTON, self.numAdd)
        self.Equ.Bind(wx.EVT_BUTTON, self.numEqu)
        
        ###### +/- and decimal buttons ######
        
        self.pos_neg = wx.Button(self.Panel2, -1, "+/-", (125,195), (50,40))
        self.decimal = wx.Button(self.Panel2, -1, ".", (180,195), (50,40))
        
        self.pos_neg.Bind(wx.EVT_BUTTON, self.pressPN)
        self.decimal.Bind(wx.EVT_BUTTON, self.pressDOT)
        
        ###### Percent and Square Root Buttons ######
        
        self.percent = wx.Button(self.Panel2, -1, "%", (125,240), (50,40))
        self.sqrt = wx.Button(self.Panel2, -1, "SqRt", (180,240), (50,40))
        
        self.percent.Bind(wx.EVT_BUTTON, self.pressPercent)
#        self.sqrt.Bind(wx.EVT_BUTTON, self.pressSqRt)
        
        ###### A Nice Picture ######
        
        pypic = wx.Bitmap("data/pyicon.png")
        wx.StaticBitmap(self.Panel2, -1, pypic, (15,230))
        
        ###### If +, -, *, /, or = pressed is set to True ######
        self.equat = False




    
    
        
    ###### -- Start Menu Handlers -- ######
    
    def Cclose(self, event):
        self.Close()
    
    def Cabout(self, event):
        AboutWXCalc = wx.MessageDialog(self,
                        "wxCalculator, written in Python with wxPython",
                        "wxCalculator", wx.OK)
        AboutWXCalc.ShowModal()
    
    ###### -- End Menu Handlers -- ######
    
    
    ###### -- Reserved for Key Pressed Event Handler -- ######
    
    
    ###### -- Start Memory Handlers -- ######
    
    def CClrM(self, event):
        self.set_mem.SetForegroundColour(wx.Colour(0,0,0))
        self.MMem = None
        return self.MMem
    
    def CSetM(self,event):
        GetCOutput = self.COutput.GetValue()
        if GetCOutput == "":
            pass
        else:
            self.set_mem.SetForegroundColour(wx.Colour(255,0,0))
            self.MMem = GetCOutput
            self.COutput.Clear()
        return self.MMem
    
    def CReadM(self, event):
        if self.MMem == None:
            pass
        else:
            self.COutput.Clear()
            self.COutput.AppendText(self.MMem)
        
    ###### -- End Memory Handlers -- ######
    
    
    ###### -- Start Clear Buttons Handlers -- ######
    
    def BackSPC(self, event):
        tmp = self.COutput.GetValue()
        if tmp == "":
            pass
        elif tmp == "0.":
            self.COutput.Clear()
        else:
            tmp2 = list(tmp)
            tmp2.pop()
            self.COutput.Clear()
            tmp3 = "".join(tmp2)
            self.COutput.write(tmp3)
    
    def ClearCE(self, event):
        self.COutput.Clear()
    
    def ClearC(self, event):
        self.COutput.Clear()
        self.CMem = []
    
    ###### -- End Clear Buttons Handlers -- ######
    
    ###### -- Start Numerical Buttons Handlers -- ######
    
    def press0(self, event):
        CVal = self.COutput.GetValue()
        if CVal == "" or self.equat == True or CVal == "-":
            pass
        else:
            if self.equat == False:
                self.COutput.AppendText("0")
            else:
                self.COutput.Clear()
                self.COutput.AppendText("0")
                self.equat = False
        return self.equat

    def press1(self, event):
        if self.equat == False:
            self.COutput.AppendText("1")
        else:
            self.COutput.Clear()
            self.COutput.AppendText("1")
            self.equat = False
        return self.equat

    def press2(self, event):
        if self.equat == False:
            self.COutput.AppendText("2")
        else:
            self.COutput.Clear()
            self.COutput.AppendText("2")
            self.equat = False
        return self.equat

    def press3(self, event):
        if self.equat == False:
            self.COutput.AppendText("3")
        else:
            self.COutput.Clear()
            self.COutput.AppendText("3")
            self.equat = False
        return self.equat

    def press4(self, event):
        if self.equat == False:
            self.COutput.AppendText("4")
        else:
            self.COutput.Clear()
            self.COutput.AppendText("4")
            self.equat = False
        return self.equat

    def press5(self, event):
        if self.equat == False:
            self.COutput.AppendText("5")
        else:
            self.COutput.Clear()
            self.COutput.AppendText("5")
            self.equat = False
        return self.equat

    def press6(self, event):
        if self.equat == False:
            self.COutput.AppendText("6")
        else:
            self.COutput.Clear()
            self.COutput.AppendText("6")
            self.equat = False
        return self.equat

    def press7(self, event):
        if self.equat == False:
            self.COutput.AppendText("7")
        else:
            self.COutput.Clear()
            self.COutput.AppendText("7")
            self.equat = False
        return self.equat

    def press8(self, event):
        if self.equat == False:
            self.COutput.AppendText("8")
        else:
            self.COutput.Clear()
            self.COutput.AppendText("8")
            self.equat = False
        return self.equat

    def press9(self, event):
        if self.equat == False:
            self.COutput.AppendText("9")
        else:
            self.COutput.Clear()
            self.COutput.AppendText("9")
            self.equat = False
        return self.equat

    ###### -- End Numerical Button Handlers -- ######
    
    ###### -- Start Equation Handlers -- ######
    
    def numAdd(self, event):
        try:
            CVal = float(self.COutput.GetValue())
            try:
                if self.equat == True:
                    self.CMem.remove(self.CMem[1])
                    self.CMem[1] = "+"
                    self.equat = True
                else:
                    self.CMem.append(str(CVal))
                    if self.CMem[1] == "+":
                        val = float(self.CMem[0]) + float(self.CMem[2])
                    elif self.CMem[1] == "-":
                        val = float(self.CMem[0]) - float(self.CMem[2])
                    elif self.CMem[1] == "*":
                        val = float(self.CMem[0]) * float(self.CMem[2])
                    elif self.CMem[1] == "/":
                        val = float(self.CMem[0]) / float(self.CMem[2])
                    self.CMem = [str(val), "+"]
                    self.COutput.Clear()
                    self.COutput.AppendText(str(val))
                    self.equat = True
            except:
                self.CMem.append("+")
                self.equat = True
        except:
            pass
        print self.CMem
        return self.equat, self.CMem
    
    def numSub(self, event):
        try:
            CVal = float(self.COutput.GetValue())
            try:
                if self.equat == True:
                    self.CMem.remove(self.CMem[1])
                    self.CMem.append("-")
                    self.equat = True
                else:
                    self.CMem.append(str(CVal))
                    if self.CMem[1] == "+":
                        val = float(self.CMem[0]) + float(self.CMem[2])
                    elif self.CMem[1] == "-":
                        val = float(self.CMem[0]) - float(self.CMem[2])
                    elif self.CMem[1] == "*":
                        val = float(self.CMem[0]) * float(self.CMem[2])
                    elif self.CMem[1] == "/":
                        val = float(self.CMem[0]) / float(self.CMem[2])
                    self.CMem = [str(val), "-"]
                    self.COutput.Clear()
                    self.COutput.AppendText(str(val))
                    self.equat = True
            except:
                self.CMem.append("-")
                self.equat = True
        except:
            pass
        print self.CMem
        return self.equat, self.CMem
        
    def numMul(self, event):
        try:
            CVal = float(self.COutput.GetValue())
            try:
                if self.equat == True:
                    self.CMem.remove(self.CMem[1])
                    self.CMem.append("*")
                    self.equat = True
                else:
                    self.CMem.append(str(CVal))
                    if self.CMem[1] == "+":
                        val = float(self.CMem[0]) + float(self.CMem[2])
                    elif self.CMem[1] == "-":
                        val = float(self.CMem[0]) - float(self.CMem[2])
                    elif self.CMem[1] == "*":
                        val = float(self.CMem[0]) * float(self.CMem[2])
                    elif self.CMem[1] == "/":
                        val = float(self.CMem[0]) / float(self.CMem[2])
                    self.CMem = [str(val), "*"]
                    self.COutput.Clear()
                    self.COutput.AppendText(str(val))
                    self.equat = True
            except:
                self.CMem.append("*")
                self.equat = True
        except:
            pass
        print self.CMem
        return self.equat, self.CMem
        
    def numDiv(self, event):
        try:
            CVal = float(self.COutput.GetValue())
            try:
                if self.equat == True:
                    self.CMem.remove(self.CMem[1])
                    self.CMem.append("/")
                    self.equat = True
                else:
                    self.CMem.append(str(CVal))
                    if self.CMem[1] == "+":
                        val = float(self.CMem[0]) + float(self.CMem[2])
                    elif self.CMem[1] == "-":
                        val = float(self.CMem[0]) - float(self.CMem[2])
                    elif self.CMem[1] == "*":
                        val = float(self.CMem[0]) * float(self.CMem[2])
                    elif self.CMem[1] == "/":
                        val = float(self.CMem[0]) / float(self.CMem[2])
                    self.CMem = [str(val), "/"]
                    self.COutput.Clear()
                    self.COutput.AppendText(str(val))
                    self.equat = True
            except:
                self.CMem.append("/")
                self.equat = True
        except:
            pass
        print self.CMem
        return self.equat, self.CMem
    
    def numEqu(self, event):
        CVal = self.COutput.GetValue()
        if self.equat == False:
            try:
                Val1 = self.CMem[0]
                Val2 = self.CMem[1]
                self.CMem = []
                if Val2 == "+":
                    FVal = float(Val1) + float(CVal)
                elif Val2 == "-":
                    FVal = float(Val1) - float(CVal)
                elif Val2 == "*":
                    FVal = float(Val1) * float(CVal)
                elif Val2 == "/":
                    FVal = float(Val1) / float(CVal)
                self.COutput.Clear()
                self.COutput.AppendText(str(FVal))
            except:
                pass
        else:
            try:
                self.CMem.remove(self.CMem[1])
                self.CMem[0] = str(float(CVal))
                self.COutput.Clear()
                self.COutput.AppendText(self.CMem[0])
            except:
                pass
    
    ###### -- End Equation Handlers -- ######
    
    ###### -- Start Others -- ######
    
    def pressPercent(self, event):
        CVal = self.COutput.GetValue()
        if CVal == "":
            pass
        else:
            PVal = float(CVal) * 0.01
            self.COutput.Clear()
            self.COutput.AppendText(str(PVal))
    
    def pressPN(self, event):
        CVal = self.COutput.GetValue()
        if "-" in CVal:
            Val1 = list(CVal)
            Val1.remove("-")
            Val2 = "".join(Val1)
            self.COutput.Clear()
            self.COutput.AppendText(Val2)
        else:
            self.COutput.Clear()
            self.COutput.AppendText("-%s" % CVal)
    
    def pressDOT(self, event):
        CVal = self.COutput.GetValue()
        if "." in CVal:
            pass
        else:
            self.COutput.AppendText(".")



class CalcApp(wx.App):
    def OnInit(self):
        Cwindow = MainWindow(None, -1, "wxCalculator")
#        Cwindow.SetBackgroundColour(wx.Colour(255,0,0))
        Cwindow.Show(True)
        self.SetTopWindow(Cwindow)
        return(True)

Cstart = CalcApp(0)
Cstart.MainLoop()[/PHP]

---

### Post by bfhicks on 2008-12-18
Just a few suggestions...

(1) You have some duplicated code in there. For example,

[php]
else:
                    self.CMem.append(str(CVal))
                    if self.CMem[1] == "+":
                        val = float(self.CMem[0]) + float(self.CMem[2])
                    elif self.CMem[1] == "-":
                        val = float(self.CMem[0]) - float(self.CMem[2])
                    elif self.CMem[1] == "*":
                        val = float(self.CMem[0]) * float(self.CMem[2])
                    elif self.CMem[1] == "/":
                        val = float(self.CMem[0]) / float(self.CMem[2])
                    self.CMem = [str(val), "+"]
                    self.COutput.Clear()
                    self.COutput.AppendText(str(val))
                    self.equat = True 
[/php]

This could be extracted to its own function to minimize duplicated code. If you found an error in one of these instances, you would have to fix it in ALL of them.. *EECK*

(2) One idea to keep in mind is GUI relationships with functionality. A calculator is a good example of this. Maybe I would want just an interactive command line calculator (I understand it's in python already, but still..) then you would have to duplicate all the mathematical part of this code! That would stink. Making a "calculator.py" class with functions such as "subtract(numberOne, numberTwo)" would allow the GUI to call those functions, and it would return the difference.


I think applying these ideas to all of your coding practices would be very beneficial in the long run as far as maintainability and extensibility.

---

### Post by matmatmat on 2008-12-18
Why not try to add exception handling - printing your own error message - would make it more user friendly, if that's what you are aiming for.

---

### Post by Bichromat on 2008-12-18
You have a bunch of pressN (N=0..9) functions that you should be able to replace by one function. This function would use the event object that is passed to it to determine which button was pressed.

---

### Post by nvteighen on 2008-12-18
> **bfhicks said:**
> Just a few suggestions...

(1) You have some duplicated code in there. For example,

[php]
else:
                    self.CMem.append(str(CVal))
                    if self.CMem[1] == "+":
                        val = float(self.CMem[0]) + float(self.CMem[2])
                    elif self.CMem[1] == "-":
                        val = float(self.CMem[0]) - float(self.CMem[2])
                    elif self.CMem[1] == "*":
                        val = float(self.CMem[0]) * float(self.CMem[2])
                    elif self.CMem[1] == "/":
                        val = float(self.CMem[0]) / float(self.CMem[2])
                    self.CMem = [str(val), "+"]
                    self.COutput.Clear()
                    self.COutput.AppendText(str(val))
                    self.equat = True 
[/php]

This could be extracted to its own function to minimize duplicated code. If you found an error in one of these instances, you would have to fix it in ALL of them.. *EECK*


To do this in a very nice way, I guess you'll have to use the operator module, which provides function equivalents to operators (such as add(), etc.). That way, you could declare a variable which will hold what function is going to be used, modify its value according to self.CMem[1] and then, call that function-variable (if you ever have done some C, this is equivalent to a pointer-to-function... if you haven't, don't care).

---

### Post by matmatmat on 2008-12-19
Why not add more functionality to the calculator, although it isn't really improving the script it would improve the calculator.

---

### Post by wmcbrine on 2008-12-19
It would be nice if you could use the keyboard as well as the on-screen buttons.

I'd make it display zero when cleared.

One thing I'd suggest for future reference is to follow [PEP 8](http://www.python.org/dev/peps/pep-0008/) where possible. In the context of your program, the relevant point is to not use CamelCase, except for class names. (wxPython itself doesn't follow this, of course, but it's not very Pythonic.)

---

