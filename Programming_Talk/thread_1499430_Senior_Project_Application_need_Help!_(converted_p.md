---
title: "Senior Project Application need Help! (converted program with py2exe, pickle error)"
date: 2010-06-01
forum: Programming Talk
---

### Post by Eremis on 2010-06-01
Hi everybody!

I am making a "food drive organizer" for my high school as my senior project. I have the 1.0.0 version finished, and Now I am converting it to an .exe (unfortunately schools use Windows...)

My program uses "pickle" module to save / open "new food drive projects". After I used py2exe to convert my program to an .exe everything works, but I can not save / open. :confused: When I exit the program I get a message box telling me that there have been errors, and to check the error log. 

Below I will post my source code to the program, setup script for py2exe, and the error log...

Can someone please help me ?!

Thanks

SOURCE CODE **********
```

#
#   Developer:      ***** ****
#
#   Project Name:   Manna Helper 1.1
#
#   File Name:      Main.py
#
#   Description:    Manna Food Bank Organizer 
#

# Imports
try:
    import wx
    import pickle
    import datetime

except:
    print 'Error: Failed to import all modules'


# A class that represents a single class
class SchoolClass:

    # Constructor 
    def __init__(self, className = 'Class Name', numStudents = 0, firstReturn = 0, secondReturn = 0,
        thirdReturn = 0, fourthReturn = 0, fifthReturn = 0):

        self.className = className
        self.numStudents = numStudents

        self.firstReturn = firstReturn
        self.secondReturn = secondReturn
        self.thirdReturn = thirdReturn
        self.fourthReturn = fourthReturn
        self.fifthReturn = fifthReturn
    
    # Functions
    def __str__(self): 

        returnStr = ''
        numLine1 = 30 - len(self.className)

        returnStr += ('' + str(self.className) + (' ' * numLine1) + str(self.numStudents) +
        (' students') + (' ' * 10) + str(self.GetTotalPounds()) + ' total pounds' + (' ' * 10) + str(self.GetRatio()) +' lb/student')

        return returnStr
    
    def GetTotalPounds(self):
        
        returnNum = (float(self.firstReturn) + float(self.secondReturn) +
        float(self.thirdReturn) + float(self.fourthReturn) + float(self.fifthReturn))
        
        return returnNum

    def GetRatio(self):

        try:
            return self.GetTotalPounds() / float(self.numStudents)

        except ArithmeticError:
            return 0
        
        
#-------------------------------------------------------------------------------

# A class that represents a year drive
class Project:
    
    # Constructor
    def __init__(self, projectName = 'Project Name'):
        now = datetime.datetime.now()
        self.projectName = projectName
        self.projectDate = now.strftime("%Y-%m-%d %H:%M")
        self.classList = {}
        self.numClasses = 0
        
    # Functions
    def AddClass(self, className = 'Class Name', numStudents = 0, firstReturn = 0, secondReturn = 0,
        thirdReturn = 0, fourthReturn = 0, fifthReturn = 0):
        
        self.classList[className] = SchoolClass(className, numStudents, firstReturn, secondReturn, thirdReturn,
            fourthReturn, fifthReturn)
        self.numClasses += 1
        
    def RemoveClass(self, className = 'Class Name'):
        
        self.classList.pop(className)
        
    def GetTotalPounds(self):
        returnNum = 0
        
        keys = self.classList.keys()
        for k in keys:
            returnNum += self.classList[k].GetTotalPounds()
        
        return returnNum
        
    def GetWinner(self):
        value1 = 0
        value2 = 0
        
        keys = self.classList.keys()
        for k in keys:
            if self.classList[k].GetRatio() > value1:
                value1 = self.classList[k].GetRatio()
                value2 = self.classList[k]
        
        return value2
        
    def __str__(self):
        
        retString = ''
        keys = self.classList.keys()
        for k in keys:
            retString += self.classList[k].__str__()
            retString += '\n'
        return retString

    
# GUI class
class MainWindow(wx.Frame):
    # Constructor
    def __init__(self, parent, id, title):
        
        # Global Variable
        self.CurrentProject = None
        self.Saved = False
        self.Directory = ''
        
        wx.Frame.__init__(self, parent, wx.ID_ANY, title = 'Manna Helper 1.1', size = (450, 500), style=wx.MINIMIZE_BOX|wx.RESIZE_BORDER|wx.SYSTEM_MENU|wx.CAPTION|wx.CLOSE_BOX|wx.CLIP_CHILDREN)
        
        panel = wx.Panel(self)          # A Panel that contains all the componets.
        self.SetIcon(wx.Icon('images/icon.ico', wx.BITMAP_TYPE_ICO))   # Set the icon
        self.SetMaxSize((450, 500))     # Set MinSize & MaxSize to same size to
        self.SetMinSize((450, 500))     #   dissable resizing.
        self.CreateStatusBar()          # Creating a Status Bar for the Main Window.
        self.Center()                   # Center the window on the screen.
        
        # Create a "File" Menu
        filemenu = wx.Menu()
        filemenu.Append(wx.ID_NEW, '&New', 'Create a new year food drive')
        filemenu.Append(wx.ID_OPEN, '&Open Existing...', 'Open an existing food drive')
        filemenu.Append(wx.ID_SAVE, '&Save', 'Save changes to the current food drive')
        filemenu.Append(wx.ID_SAVEAS, 'S&ave As', 'Save as a new year food drive')
        filemenu.Append(wx.ID_PROPERTIES, '&Project Properties', 'View the properties of this project')
        filemenu.AppendSeparator()
        filemenu.Append(wx.ID_EXIT, 'E&xit', 'Exit the application')
        
        # Create an "Edit" Menu
        editmenu = wx.Menu()
        editmenu.Append(wx.ID_ADD, '&Add Class', 'Add new class to current project')
        editmenu.Append(wx.ID_REMOVE, '&Remove Class', 'Remove selected class from current project')
        editmenu.Append(wx.ID_EDIT, '&Edit Class', 'Edit selected class')
        editmenu.Append(wx.ID_PREVIEW, '&Generate Results', 'Generate text file with results')
        
        # Create a "Help" Menu
        helpmenu = wx.Menu()
        helpmenu.Append(wx.ID_ABOUT, '&About', 'Information about this program')
        
        # Create a ManuBar
        menubar = wx.MenuBar()
        menubar.Append(filemenu, '&File')
        menubar.Append(editmenu, '&Edit')
        menubar.Append(helpmenu, '&Help')
        self.SetMenuBar(menubar)
        
        # Create Buttons
        defaultSize = (100, 30)
        addButton = wx.Button(panel, id = wx.ID_ADD, label = 'Add Class', pos = (10, 340), size = defaultSize)
        removeButton = wx.Button(panel, id = wx.ID_REMOVE, label = 'Remove Class', pos = (120, 340), size = defaultSize)
        generateButton = wx.Button(panel, id = wx.ID_PREVIEW, label = 'Generate Result File', pos = (10, 380), size = (210, 30))
        editButton = wx.Button(panel, id = wx.ID_EDIT, label = 'Edit Class', pos = (320, 340), size = (100, 70))
        
        # Setting button event handlers
        wx.EVT_BUTTON(self, wx.ID_ADD, self.OnAdd)
        wx.EVT_BUTTON(self, wx.ID_REMOVE, self.OnRemove)
        wx.EVT_BUTTON(self, wx.ID_PREVIEW, self.OnGenerateResults)
        wx.EVT_BUTTON(self, wx.ID_EDIT, self.OnEdit)
        
        # Setting menu event handlers
        wx.EVT_MENU(self, wx.ID_NEW, self.OnNew)
        wx.EVT_MENU(self, wx.ID_OPEN, self.OnOpen)
        wx.EVT_MENU(self, wx.ID_SAVE, self.OnSave)
        wx.EVT_MENU(self, wx.ID_SAVEAS, self.OnSaveAs)
        wx.EVT_MENU(self, wx.ID_PROPERTIES, self.OnProperties)
        wx.EVT_MENU(self, wx.ID_EXIT, self.OnExit)
        wx.EVT_MENU(self, wx.ID_ADD, self.OnAdd)
        wx.EVT_MENU(self, wx.ID_REMOVE, self.OnRemove)
        wx.EVT_MENU(self, wx.ID_EDIT, self.OnEdit)
        wx.EVT_MENU(self, wx.ID_PREVIEW, self.OnGenerateResults)
        wx.EVT_MENU(self, wx.ID_ABOUT, self.OnAbout)
        
        # Create a list
        self.Classes = wx.ListCtrl(panel, -1, style=wx.LC_REPORT, pos = (10, 10), size = (410, 320))
        self.Classes.InsertColumn(0, 'Class Name')
        self.Classes.InsertColumn(1, 'Number Students')
        self.Classes.InsertColumn(2, 'Lb/Student')
        self.Classes.InsertColumn(3, '1st')
        self.Classes.InsertColumn(4, '2nd')
        self.Classes.InsertColumn(5, '3rd')
        self.Classes.InsertColumn(6, '4th')
        self.Classes.InsertColumn(7, '5th')
        
        # Edit list width
        self.Classes.SetColumnWidth(0, 180)
        self.Classes.SetColumnWidth(1, 130)
        self.Classes.SetColumnWidth(2, 100)
        self.Classes.SetColumnWidth(3, 82)
        self.Classes.SetColumnWidth(4, 82)
        self.Classes.SetColumnWidth(5, 82)
        self.Classes.SetColumnWidth(6, 82)
        self.Classes.SetColumnWidth(7, 82)
        
        # Setting close button event handler
        wx.EVT_CLOSE(self, self.CloseWindow)
        
        # Show the Frame
        self.Show(True)
        
    # Event Handlers
    def OnNew(self, event):
        print 'Creating a new project...'
        
        self.Classes.DeleteAllItems()
        
        NewDlg = wx.TextEntryDialog(self, 'Enter project name:','New Project...')
        
        if NewDlg.ShowModal() == wx.ID_OK:
            
            if NewDlg.GetValue() == None or NewDlg.GetValue() == '':
                ErrorDlg = wx.MessageDialog(None, 'Invalid Name', 'Error: Invalid Name', wx.OK)
                ErrorDlg.ShowModal()
                ErrorDlg.Destroy()
                print 'No project made due to \"Invalid Project Name Error\"'
            
            else:
                projectName = NewDlg.GetValue()
                self.CurrentProject = Project(projectName)
                print 'New project \"' + projectName +'" created!'
        else:
            print 'No project made due to \"New Project Error\"'
            
        NewDlg.Destroy()     
 
    def OnOpen(self, event):
        print 'Opening project...' 
        
        self.Classes.DeleteAllItems()
        
        filters = 'Project files (*.pkl)|*.pkl|All files (*.*)|*.*'
        SaveDlg = wx.FileDialog ( None, message = 'Open something....', wildcard = filters, style = wx.OPEN)
        
        if SaveDlg.ShowModal() == wx.ID_OK:
            selection = SaveDlg.GetPath()
            print 'Selected: ', selection
            F = open(selection, 'rb')
            openedProject = pickle.load(F)
            self.CurrentProject = openedProject
            print 'Opened Project: \"' + selection + '\"'
            
            for keys in self.CurrentProject.classList.keys():
                num_items = self.Classes.GetItemCount()
                self.Classes.InsertStringItem(num_items, str(self.CurrentProject.classList[keys].className))
                self.Classes.SetStringItem(num_items, 1, str(self.CurrentProject.classList[keys].numStudents))
                self.Classes.SetStringItem(num_items, 2, str(self.CurrentProject.classList[keys].GetRatio()))
                self.Classes.SetStringItem(num_items, 3, str(self.CurrentProject.classList[keys].firstReturn))
                self.Classes.SetStringItem(num_items, 4, str(self.CurrentProject.classList[keys].secondReturn))
                self.Classes.SetStringItem(num_items, 5, str(self.CurrentProject.classList[keys].thirdReturn))
                self.Classes.SetStringItem(num_items, 6, str(self.CurrentProject.classList[keys].fourthReturn))
                self.Classes.SetStringItem(num_items, 7, str(self.CurrentProject.classList[keys].fifthReturn))
            print 'New class added!'
            self.Directory = selection
            self.Saved = True
            
        else:
           print 'Nothing was selected.'
        
        SaveDlg.Destroy()
        
    def OnSave(self, event):
        print 'Saving changes...'
        if self.Saved == False:
            ErrorDial = wx.MessageDialog(None, 'Save As first!', 'Error: Save Project', wx.OK)
            ErrorDial.ShowModal()
            ErrorDial.Destroy()
            print 'Project not saved due to \"Save Project Error\"'
        else:
            F = open(self.Directory, 'wb')
            pickle.dump(self.CurrentProject, F)
            F.close()
            print 'Saved Changes'
            
        
    def OnSaveAs(self, event):
        print 'Saving as a new project...'
        
        if self.CurrentProject == None:
            ErrorDial = wx.MessageDialog(None, 'Create or open project first!', 'Error: No Project', wx.OK)
            ErrorDial.ShowModal()
            ErrorDial.Destroy()
            print 'Project not saved due to \"No Project Error\"'
        
        else:
            SaveAsDlg = wx.FileDialog (self, style = wx.SAVE)
            
            if SaveAsDlg.ShowModal() == wx.ID_OK:
               print 'Selected:', SaveAsDlg.GetPath() + '.pkl'
               F = open((SaveAsDlg.GetPath() + '.pkl'), 'wb')
               pickle.dump(self.CurrentProject, F)
               F.close()
               self.Saved = True
               self.Directory = (SaveAsDlg.GetPath() + '.pkl')
               print 'Project saved as \"' + (SaveAsDlg.GetPath() + '.pkl') + '\"'
               
            else:
               print 'Nothing was selected.'

            SaveAsDlg.Destroy()
        
    def OnProperties(self, event):
        print 'Generating Project Properties'
        if self.CurrentProject == None:
            ErrorDial = wx.MessageDialog(None, 'Create a new project first!', 'Error: New Project', wx.OK)
            ErrorDial.ShowModal()
            ErrorDial.Destroy()
            print 'Class not added due to \"No Project Error\"'
        else:
            properties = ('Project Name:        ' + self.CurrentProject.projectName +
                      '\n\nDate Created:        ' + self.CurrentProject.projectDate +
                      '\n\nNumber of Classes:  ' + str(self.CurrentProject.numClasses) +
                      '\n\nTotal Pounds Collected:  ' + str(self.CurrentProject.GetTotalPounds()) +
                      '\n\n________________________________\n\n' + 'The Overall Winner:     ' +
                      self.CurrentProject.GetWinner().className + ' with ratio of ' + str(self.CurrentProject.GetWinner().GetRatio()) + ' lb/student')
            PropDlg = wx.MessageDialog(None, properties, 'Project Properties', wx.OK)
            PropDlg.ShowModal()
            PropDlg.Destroy()

        
    def OnExit(self, event):
        print 'Exiting...'
        self.Close(True)
        
    
    def OnAdd(self, event):
        print 'Adding new class...'
        if self.CurrentProject == None:
            ErrorDial = wx.MessageDialog(None, 'Create a new project first!', 'Error: New Project', wx.OK)
            ErrorDial.ShowModal()
            ErrorDial.Destroy()
            print 'Class not added due to \"No Project Error\"'

        else:
            dlgName = wx.TextEntryDialog(self, 'Enter class name:','Add Class...')
            if dlgName.ShowModal() == wx.ID_OK:
                className = dlgName.GetValue()
                
                dlgNumber = wx.TextEntryDialog(self, 'Enter number of students:','Add Class...')
                if dlgNumber.ShowModal() == wx.ID_OK:
                    numberStudents = dlgNumber.GetValue()
                    
                    dlgFirst = wx.TextEntryDialog(self, 'Pounds in 1st turn-in:','Add Class...')
                    if dlgFirst.ShowModal() == wx.ID_OK:
                        first = dlgFirst.GetValue()
                        
                        dlgSecond = wx.TextEntryDialog(self, 'Pounds in 2nd turn-in:','Add Class...')
                        if dlgSecond.ShowModal() == wx.ID_OK:
                            second = dlgSecond.GetValue()
                            
                            dlgThird = wx.TextEntryDialog(self, 'Pounds in 3rd turn-in:','Add Class...')
                            if dlgThird.ShowModal() == wx.ID_OK:
                                third = dlgThird.GetValue()
                                            
                                dlgFourth = wx.TextEntryDialog(self, 'Pounds in 4th turn-in:','Add Class...')
                                if dlgFourth.ShowModal() == wx.ID_OK:
                                    fourth = dlgFourth.GetValue()
                                            
                                    dlgFifth = wx.TextEntryDialog(self, 'Pounds in 5th turn-in:','Add Class...')
                                    if dlgFifth.ShowModal() == wx.ID_OK:
                                        fifth = dlgFifth.GetValue()
                                    dlgFifth.Destroy()    
                                dlgFourth.Destroy()      
                            dlgThird.Destroy()    
                        dlgSecond.Destroy()
                    dlgFirst.Destroy()
                dlgNumber.Destroy()
            dlgName.Destroy()

            try:
                className
                numberStudents
                first
                second
                third
                fourth
                fifth
                
                self.CurrentProject.AddClass(className, numberStudents, first, second, third, fourth, fifth)
                num_items = self.Classes.GetItemCount()
                self.Classes.InsertStringItem(num_items, className)
                self.Classes.SetStringItem(num_items, 1, numberStudents)
                self.Classes.SetStringItem(num_items, 2, str(self.CurrentProject.classList[className].GetRatio()))
                self.Classes.SetStringItem(num_items, 3, str(self.CurrentProject.classList[className].firstReturn))
                self.Classes.SetStringItem(num_items, 4, str(self.CurrentProject.classList[className].secondReturn))
                self.Classes.SetStringItem(num_items, 5, str(self.CurrentProject.classList[className].thirdReturn))
                self.Classes.SetStringItem(num_items, 6, str(self.CurrentProject.classList[className].fourthReturn))
                self.Classes.SetStringItem(num_items, 7, str(self.CurrentProject.classList[className].fifthReturn))
                print 'New class added!' 
                
            except NameError:
                ErrorDial = wx.MessageDialog(None, 'Variable not specified!', 'Error: Variable Not Given', wx.OK)
                ErrorDial.ShowModal()
                ErrorDial.Destroy()
                print 'Class not added due to \"No Name Given Error\"'
        
    def OnRemove(self, event):
        print 'Removing class...'
        if self.CurrentProject == None:
            ErrorDial = wx.MessageDialog(None, 'Create a new project first!', 'Error: New Project', wx.OK)
            ErrorDial.ShowModal()
            ErrorDial.Destroy()
            print 'Class not deleted due to \"No Project Error\"'

        else:
            try:
                index = self.Classes.GetFocusedItem()
                name = str(self.Classes.GetItemText(index))
                self.CurrentProject.RemoveClass(name)
                self.Classes.DeleteItem(index)
                print 'Removed class \"' + name + '\"'
            except:
                ErrorDial = wx.MessageDialog(None, 'Select a class to delete!', 'Error: No class selected', wx.OK)
                ErrorDial.ShowModal()
                ErrorDial.Destroy()
                print 'Class not deleted due to \"No Project Selected Error\"'
            
    def OnEdit(self, event):
        print 'Editing class...'
        if self.CurrentProject == None:
            ErrorDial = wx.MessageDialog(None, 'Create a new project first!', 'Error: New Project', wx.OK)
            ErrorDial.ShowModal()
            ErrorDial.Destroy()
            print 'Class not added due to \"No Project Error\"'
            
        else:
            index = self.Classes.GetFocusedItem()
            name = str(self.Classes.GetItemText(index))
            
            #dlgName = wx.TextEntryDialog(self, 'Enter class name:','Edit Class...')
            #dlgName.SetValue(str(self.CurrentProject.classList[name].className))
            #if dlgName.ShowModal() == wx.ID_OK:
            #    className = str(dlgName.GetValue())
                
            dlgNumber = wx.TextEntryDialog(self, 'Enter number of students:','Edit Class...')
            dlgNumber.SetValue(str(self.CurrentProject.classList[name].numStudents))
            if dlgNumber.ShowModal() == wx.ID_OK:
                numberStudents = dlgNumber.GetValue()
                
                dlgFirst = wx.TextEntryDialog(self, 'Pounds in 1st turn-in:','Edit Class...')
                dlgFirst.SetValue(str(self.CurrentProject.classList[name].firstReturn))
                if dlgFirst.ShowModal() == wx.ID_OK:
                    first = dlgFirst.GetValue()
                    
                    dlgSecond = wx.TextEntryDialog(self, 'Pounds in 2nd turn-in:','Edit Class...')
                    dlgSecond.SetValue(str(self.CurrentProject.classList[name].secondReturn))
                    if dlgSecond.ShowModal() == wx.ID_OK:
                        second = dlgSecond.GetValue()
                        
                        dlgThird = wx.TextEntryDialog(self, 'Pounds in 3rd turn-in:','Edit Class...')
                        dlgThird.SetValue(str(self.CurrentProject.classList[name].thirdReturn))
                        if dlgThird.ShowModal() == wx.ID_OK:
                            third = dlgThird.GetValue()
                                        
                            dlgFourth = wx.TextEntryDialog(self, 'Pounds in 4th turn-in:','Edit Class...')
                            dlgFourth.SetValue(str(self.CurrentProject.classList[name].fourthReturn))
                            if dlgFourth.ShowModal() == wx.ID_OK:
                                fourth = dlgFourth.GetValue()
                                        
                                dlgFifth = wx.TextEntryDialog(self, 'Pounds in 5th turn-in:','Edit Class...')
                                dlgFifth.SetValue(str(self.CurrentProject.classList[name].fifthReturn))
                                if dlgFifth.ShowModal() == wx.ID_OK:
                                    fifth = dlgFifth.GetValue()
                                dlgFifth.Destroy()    
                            dlgFourth.Destroy()      
                        dlgThird.Destroy()    
                    dlgSecond.Destroy()
                dlgFirst.Destroy()
            dlgNumber.Destroy()
            #dlgName.Destroy()
            
            try:
                numberStudents
                first
                second
                third
                fourth
                fifth
            
                self.CurrentProject.classList[name].className = name
                self.CurrentProject.classList[name].numStudents = numberStudents
                self.CurrentProject.classList[name].firstReturn = first
                self.CurrentProject.classList[name].secondReturn = second
                self.CurrentProject.classList[name].thirdReturn = third
                self.CurrentProject.classList[name].fourthReturn = fourth
                self.CurrentProject.classList[name].fifthReturn = fifth
                
                self.Classes.SetStringItem(index, 0, name)
                self.Classes.SetStringItem(index, 1, numberStudents)
                self.Classes.SetStringItem(index, 2, str(self.CurrentProject.classList[name].GetRatio()))
                self.Classes.SetStringItem(index, 3, first)
                self.Classes.SetStringItem(index, 4, second)
                self.Classes.SetStringItem(index, 5, third)
                self.Classes.SetStringItem(index, 6, fourth)
                self.Classes.SetStringItem(index, 7, fifth)
    
                print 'Class edited'
            
            except NameError:
                ErrorDial = wx.MessageDialog(None, 'Variable not specified!', 'Error: Variable Not Given', wx.OK)
                ErrorDial.ShowModal()
                ErrorDial.Destroy()
                print 'Class not edited due to \"No Name Given Error\"'

    def OnSort(self, event):
        print 'Sort'
        
    def OnGenerateResults(self, event):
        print 'Generating File...'
        
        if self.CurrentProject == None:
            ErrorDial = wx.MessageDialog(None, 'Create a new project first!', 'Error: New Project', wx.OK)
            ErrorDial.ShowModal()
            ErrorDial.Destroy()
            print 'Class not added due to \"No Project Error\"'
        
        else:
            GenerateDlg = wx.FileDialog (self, style = wx.SAVE)
                
            if GenerateDlg.ShowModal() == wx.ID_OK:
               print 'Selected:', GenerateDlg.GetPath() + '.txt'
               F = open((GenerateDlg.GetPath() + '.txt'), 'w')
               # Write the file
               
               generatedString = ''
               generatedString += '---------------------------------------------------------------------------------------------\n'
               generatedString += '                                                                                           \n'
               generatedString += '                          Generated File for Project: ' + self.CurrentProject.projectName + '\n'
               generatedString += '                                                                                           \n'
               generatedString += '---------------------------------------------------------------------------------------------\n'
               
               generatedString += '\n\n\nProject Results:\n\n'
               generatedString += self.CurrentProject.__str__()
               generatedString += '\n\n\n---------------------------------------------------------------------------------------------\n'
               generatedString += '\n\nTotal Pounds Collected: ' + str(self.CurrentProject.GetTotalPounds()) + ' lb'
               generatedString += '\n\nThe Overall Winner: ' + self.CurrentProject.GetWinner().className
               
               F.write(generatedString)
               
               F.close()

               print 'File generated at \"' + (GenerateDlg.GetPath() + '.txt') + '\"'
               
            else:
               print 'Nothing was selected.'
    
            GenerateDlg.Destroy()
        
    def OnAbout(self, event):
        print 'About'
        description = """Manna Helper is an advanced organizing
        application. It features the ability to create new \"Projects\"
        (Yearly Food Drives), and add classes with diffrent variables
        such as: number of students per class and amounts of pounds
        collected by each class. This application also includes the
        ability to open/save new projects or current projects."""
        
        licence = """Manna Helper is free software; you can redistribute it and/or modify it 
        under the terms of the GNU General Public License as published by the Free Software Foundation; 
        either version 2 of the License, or (at your option) any later version.
        
        Manna Helper is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; 
        without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  
        See the GNU General Public License for more details. You should have received a copy of 
        the GNU General Public License along with File Hunter; if not, write to 
        the Free Software Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA"""
        
        info = wx.AboutDialogInfo()

        info.SetIcon(wx.Icon('images/image.png', wx.BITMAP_TYPE_PNG))
        info.SetName('Manna Helper')
        info.SetVersion('1.1')
        info.SetDescription(description)
        info.SetCopyright('(C) 2010 ***** ****')
        info.SetWebSite('http://manna-helper.webs.com')
        info.SetLicence(licence)
        info.AddDeveloper('***** ****')

        wx.AboutBox(info)


    
    def CloseWindow(self, event):
        print 'Close Window Button'
        print 'Exit'
        print 'Save changes?'
        dlg = wx.MessageDialog(self, 'Would you like to save changes?','Save?', wx.YES | wx.NO | wx.ICON_INFORMATION)
        result = dlg.ShowModal()
        if  result == wx.ID_YES:
            print 'Save...'
            
            if self.Saved == True:
                self.OnSave(self)
            else:
                self.OnSaveAs(self)
        elif result == wx.ID_NO:
            print 'Not Save, just exit...'
        dlg.Destroy()
        self.Destroy()


# Program Runner     
app = wx.PySimpleApp()
frame = MainWindow(None, -1, 'Manna Helper 1.1')
app.MainLoop()


```

ERROR LOG **********
```

Traceback (most recent call last):
  File "Main.py", line 257, in OnOpen
  File "pickle.pyo", line 1370, in load
  File "pickle.pyo", line 858, in load
  File "pickle.pyo", line 971, in load_string
LookupError: unknown encoding: string-escape
Traceback (most recent call last):
  File "Main.py", line 257, in OnOpen
  File "pickle.pyo", line 1370, in load
  File "pickle.pyo", line 858, in load
  File "pickle.pyo", line 971, in load_string
LookupError: unknown encoding: string-escape
Traceback (most recent call last):
  File "Main.py", line 309, in OnSaveAs
  File "pickle.pyo", line 1362, in dump
  File "pickle.pyo", line 224, in dump
  File "pickle.pyo", line 286, in save
  File "pickle.pyo", line 725, in save_inst
  File "pickle.pyo", line 286, in save
  File "pickle.pyo", line 649, in save_dict
  File "pickle.pyo", line 663, in _batch_setitems
  File "pickle.pyo", line 286, in save
  File "pickle.pyo", line 500, in save_unicode
LookupError: unknown encoding: raw-unicode-escape
Traceback (most recent call last):
  File "Main.py", line 257, in OnOpen
  File "pickle.pyo", line 1370, in load
  File "pickle.pyo", line 858, in load
  File "pickle.pyo", line 971, in load_string
LookupError: unknown encoding: string-escape
Traceback (most recent call last):
  File "Main.py", line 257, in OnOpen
  File "pickle.pyo", line 1370, in load
  File "pickle.pyo", line 858, in load
  File "pickle.pyo", line 971, in load_string
LookupError: unknown encoding: string-escape

```

SETUP FILE **********
```

# Py2Exe version 0.6.3 setup file for console programs.
# If this is a windows GUI application replace the last line with
# windows = [{"script": 'myFile.py'}] )
#
# Enter the file name of your own .py code file in the last line, lets say it's test1.py
# so the last line should be: console = [{"script": 'test1.py'}] )
# then save this program as   p2e_test1.py  to the same directory where your code file is located
# Now run p2e_test1.py ...
#
# Two subfolders will be created, called  build and  dist.
# The dist folder contains your .exe file, MSVCR71.dll and w9xpopen.exe (needed for os.popen() only)
# Your .exe file contains your byte code, all needed modules and the Python interpreter.
# The MSVCR71.dll can be distributed, but is often already in the system32 folder.
# The build folder can be deleted.
# tested with Python24 and Py2Exe v0.6.3 by   vegaseat   27may2006

from distutils.core import setup
import py2exe
import sys
import wx
import pickle 

# no arguments
if len(sys.argv) == 1:
    sys.argv.append("py2exe")

# creates a standalone .exe file, no zip files
setup( options = {"py2exe": {"compressed": 1, "optimize": 2, "ascii": 1, "bundle_files": 1}},
       zipfile = None,
       # replace myFile.py with your own code filename here ...
       windows = [{"script": 'Main.py'}] )


```

---

### Post by raydeen on 2010-06-02
Just a hunch from taking a quick look, but I *think* the error may be stemming from lines like these:

            print 'Class not added due to \"No Project Error\"'

I'm not sure why you're adding a '\' in these lines. I wouldn't think you'd have to as the double quotes should be legal as your print statement is ultimately using single quotes. I think maybe the program is getting hung up trying to figure out why you have the slash in there. There errors are reporting an unknown string escape sequence. 

I"m a newbie so I could be on the wrong track. (usually am)

---

### Post by zarqoon on 2010-06-02
Raydeen is quite right and you do not need the backslash characters to escape your quotes. But python is able to handle the escaped quotes and they should not be a problem. 
I have no idea why your error occurs but there may be another solution.
There is no reason windows machines can not run python code. You just have to install a python interpreter. There is an installer available at python.org.

---

### Post by soltanis on 2010-06-02
If you need to deploy across many machines then installing Python on all of them is not very feasible.

If you are using a simple format for storing your data (like a dictionary or list or some other combination of Python primitives) then consider using a different format (other than pickle) for storing your data. In particular, if you use Python 2.6 or higher, you should have JSON available to you (via the json module) which uses this very handy data serialization format.

No idea if it will fix your errors, per se, however. I didn't read through all your code.

---

### Post by Eremis on 2010-06-02
Thanks for all the replies, but i solved my problem...
The problem was in the setup file, because it did not include encoding module...

Below is the solution:

```

# Py2Exe version 0.6.3 setup file for console programs.
# If this is a windows GUI application replace the last line with
# windows = [{"script": 'myFile.py'}] )
#
# Enter the file name of your own .py code file in the last line, lets say it's test1.py
# so the last line should be: console = [{"script": 'test1.py'}] )
# then save this program as   p2e_test1.py  to the same directory where your code file is located
# Now run p2e_test1.py ...
#
# Two subfolders will be created, called  build and  dist.
# The dist folder contains your .exe file, MSVCR71.dll and w9xpopen.exe (needed for os.popen() only)
# Your .exe file contains your byte code, all needed modules and the Python interpreter.
# The MSVCR71.dll can be distributed, but is often already in the system32 folder.
# The build folder can be deleted.
# tested with Python24 and Py2Exe v0.6.3 by   vegaseat   27may2006

from distutils.core import setup
import py2exe
import sys
import wx

# no arguments
if len(sys.argv) == 1:
    sys.argv.append("py2exe")

# creates a standalone .exe file, no zip files
setup( options = {"py2exe": {"compressed": 1, "optimize": 2, "ascii": 1, "bundle_files": 1, }},
       zipfile = None,"packages": ["encodings"]
       # replace myFile.py with your own code filename here ...
       windows = [{"script": 'Main.py'}] )

```

Notice how I added 
```

"packages": ["encodings"]

```

This solved my problem...
Here's where I got the information from:
[http://www.py2exe.org/index.cgi/EncodingsAgain](http://www.py2exe.org/index.cgi/EncodingsAgain)

Once again thanks for replies!:P

---

