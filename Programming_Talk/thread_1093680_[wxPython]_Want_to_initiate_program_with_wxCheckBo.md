---
title: "[wxPython] Want to initiate program with wxCheckBox &quot;checked&quot;"
date: 2009-03-11
forum: Programming Talk
---

### Post by dodle on 2009-03-11
[PHP]#! /usr/bin/env python

from wxPython.wx import *

ID_About = 101
ID_Exit = 102

class MainWindow(wxFrame):
    def __init__(self, parent, id, title):
        wxFrame.__init__(self, parent, id, title, wxPoint(100,200), wxSize(500,300))
        
        ## Create the status bar
        self.CreateStatusBar()
        self.SetStatusText("Monthy Payment Checklist")
        
        ## Create the menu bar
        menu = wxMenu()
        menu.Append(ID_About, "&About")
        menu.AppendSeparator()
        menu.Append(ID_Exit, "E&xit")
        
        menu_bar = wxMenuBar()
        menu_bar.Append(menu, "&File")
        
        self.SetMenuBar(menu_bar)
        
        ## Create the main window
        self.mainWindow = wxPanel(self, -1)
        wxStaticText(self.mainWindow, -1, "Car", (5,10))
        
        self.carBox = wxCheckBox(self.mainWindow, -1, "Paid", (100,10))
        EVT_MENU(self, ID_Exit, self.onExit)
        
        try:
            dataFile = open("data", "r")
            dataFile.read()
            carVal = dataFile.getline(1)
            if carVal == "car1":
                self.carBox.SetValue(True)
            else:
                pass

        except:
            dataFile = open("data", "w")
            dataFile.write("car0")
            
        saveB = wxButton(self.mainWindow, -1, "Save", (110,110), (-1,-1))
        
        saveB.Bind(EVT_BUTTON, self.saveIT)
        
        
    def onExit(self, event):
        self.Close(True)
    
    def saveIT(self, event):
        carVal = self.carBox.GetValue()
        dataFile = open("data", "w")
        if carVal == True:
            dataFile.write("car1")
        else:
            dataFile.write("car0")

class App(wxApp):
    def OnInit(self):
        frame = MainWindow(NULL, -1, "Monthly Payment Checklist")
        frame.Show(True)
        self.SetTopWindow(frame)
        return true

app = App(0)
app.MainLoop()[/PHP]How do I set the value of the check box to checked upon initializing to program?[PHP]try:
    dataFile = open("data", "r")
    dataFile.read()
    carVal = dataFile.getline(1)
    if carVal == "car1":
        self.carBox.SetValue(True)
    else:
        pass[/PHP]

---

### Post by dodle on 2009-03-11
Here is the code with the solution that I found:[php]#! /usr/bin/env python

import wx

ID_About = 101
ID_Exit = 102


class MainWindow(wx.Frame):
    def __init__(self, parent, id, title):
        wx.Frame.__init__(self, parent, id, title, wx.Point(100,200), wx.Size(500,300))
        
        ## Create the status bar
        self.CreateStatusBar()
        self.SetStatusText("Monthy Payment Checklist")
        
        ## Create the menu bar
        menu = wx.Menu()
        menu.Append(ID_About, "&About")
        menu.AppendSeparator()
        menu.Append(ID_Exit, "E&xit")
        
        menu_bar = wx.MenuBar()
        menu_bar.Append(menu, "&File")
        
        self.SetMenuBar(menu_bar)
        
        ## Create the main window
        self.mainWindow = wx.Panel(self, -1)
        wx.StaticText(self.mainWindow, -1, "Car\n\nHouse", (5,10))
        
        self.carBox = wx.CheckBox(self.mainWindow, -1, "Paid", (100,10))
        self.housBox = wx.CheckBox(self.mainWindow, -1, "Paid", (100,30))
        
        wx.EVT_MENU(self, ID_Exit, self.onExit)
        
        try:
            dataFile = open("data", "r")
            payVal = dataFile.read()
            self.payList = payVal.split("\n")
            print payVal
            dataFile.close()

        except:
            self.payList = ["car0", "hous0"]
            dataFile = open("data", "w")
            dataFile.write("%s\n%s\n" % (self.payList[0],self.payList[1]))
            dataFile.close
            
        saveB = wx.Button(self.mainWindow, -1, "Save", (110,110), (-1,-1))
        
        saveB.Bind(wx.EVT_BUTTON, self.saveIT)

        print self.payList
        if self.payList[0] == "car1":
            self.carBox.SetValue(True)
        if self.payList[1] == "hous1":
            self.housBox.SetValue(True)
            
        def sav(self):
            self.car = self.carBox.GetValue()
            if self.car == True:
                self.payList[0] = "car1"
            else:
                self.payList[0] = "car0"
            self.house = self.housBox.GetValue()
            if self.house == True:
                self.payList[1] = "hous1"
            else:
                self.payList[1] = "hous0"
            return self
        self.sav = sav(self)
        
        
        
    def onExit(self, event):
        self.Close(True)
    
    def saveIT(self, event):
        #getStuff = self.sav
        carVal = self.carBox.GetValue()
        if carVal == True:
            self.payList[0] = "car1"
        else:
            self.payList[0] = "car0"
        housVal = self.housBox.GetValue()
        if housVal == True:
            self.payList[1] = "hous1"
        else:
            self.payList[1] = "hous0"
        dataFile = open("data", "w")
        dataFile.write("%s\n%s\n" % (self.payList[0],self.payList[1]))
        dataFile.close
        return self

class App(wx.App):
    def OnInit(self):
        frame = MainWindow(None, -1, "Monthly Payment Checklist")
        frame.Show(True)
        self.SetTopWindow(frame)
        return True

app = App(0)
app.MainLoop()[/php]

---

