---
title: "first pyQT program"
date: 2009-03-08
forum: Programming Talk
---

### Post by lapubell on 2009-03-08
hello all.  I'm working on my first little pyQT app and am having trouble with the polishing touches.

the layout was made in QT3 Designer and i've written out some of the functionality but don't know how to accomplish a few things.  There are many good tutorials, but i'm not used to anything C/C++ related, as i never code in them.  Does anyone know of a good online documentation?  The tutorials are great, and it's how i've gotten this far, but they mostly only point out how to do things with the QT Elements that the tutorial uses.

anyway, here is my code.  The only things that I really need to do to finish this little guy off is make the program close after exectuing the code when the OK button are clicked, and have the selected text be the default cursor position, instead of the frist radio button.

any help, or a point in the right direction?
```

#! /usr/bin/python

from qt import *
import sys, os, urllib2


class NewSite(QMainWindow):
    def __init__(self,parent = None,name = None,fl = 0):
        QMainWindow.__init__(self,parent,name,fl)
        self.statusBar()

        if not name:
            self.setName("NewSite")

        self.setCentralWidget(QWidget(self,"qt_central_widget"))

        self.buttonGroup1 = QButtonGroup(self.centralWidget(),"buttonGroup1")
        self.buttonGroup1.setGeometry(QRect(20,49,121,70))
        self.xhtmlRadio = QRadioButton(self.buttonGroup1,"xhtmlRadio")
        self.xhtmlRadio.setGeometry(QRect(10,21,104,20))
        self.xhtmlRadio.setChecked(1)
        self.htmlRadio = QRadioButton(self.buttonGroup1,"htmlRadio")
        self.htmlRadio.setGeometry(QRect(10,41,104,20))

        self.cssBox = QCheckBox(self.centralWidget(),"cssBox")
        self.cssBox.setGeometry(QRect(150,70,120,21))
        self.cssBox.setChecked(1)
        self.jqueryBox = QCheckBox(self.centralWidget(),"jqueryBox")
        self.jqueryBox.setGeometry(QRect(150,90,120,21))
        self.jqueryBox.setChecked(1)

        self.cancelButton = QPushButton(self.centralWidget(),"cancelButton")
        self.cancelButton.setGeometry(QRect(20,130,121,31))
        self.okButton = QPushButton(self.centralWidget(),"okButton")
        self.okButton.setGeometry(QRect(150,130,111,31))

        self.siteName = QLineEdit(self.centralWidget(),"siteName")
        self.siteName.setGeometry(QRect(20,5,241,31))

        self.languageChange()

        self.resize(QSize(284,191).expandedTo(self.minimumSizeHint()))
        self.clearWState(Qt.WState_Polished)

        self.connect(self.okButton,SIGNAL("clicked()"),self.ok_clicked)
        self.connect(self.cancelButton,SIGNAL("clicked()"),self.close)
        self.siteName.selectAll()

    def languageChange(self):
        self.setCaption(self.__tr("Create A New Site"))
        self.siteName.setText(self.__tr("name of new site"))
        self.buttonGroup1.setTitle(self.__tr("DOCTYPE"))
        self.xhtmlRadio.setText(self.__tr("&XHTML"))
        self.htmlRadio.setText(self.__tr("&HTML 4"))
        self.cssBox.setText(self.__tr("Include C&SS"))
        self.jqueryBox.setText(self.__tr("Include &jQuery"))
        self.cancelButton.setText(self.__tr("&Cancel"))
        self.okButton.setText(self.__tr("&OK"))

    def ok_clicked(self):
        siteFolder = self.siteName.text()
        os.mkdir(siteFolder) #create new site folder
        
        if self.xhtmlRadio.isChecked():
            doctypeStr = '<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">\n<html xmlns="http://www.w3.org/1999/xhtml">\n\n<head>\n    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />\n    <title></title>\n'
        else:
            doctypeStr = '<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">\n\n<html>\n    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">\n\n<head>\n    <title></title>\n'
        indexFile = open(siteFolder+"/index.php", "w")
        indexFile.write(doctypeStr)
        
        if self.jqueryBox.isChecked():
            os.mkdir(siteFolder+"/js")
            url = "http://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js"
            responce = urllib2.urlopen(url)
            jqueryFromWeb = responce.read()
            jqueryFile = open(siteFolder+"/js/jquery.js", "w")
            jqueryFile.write(jqueryFromWeb)
            jsfunctions = open(siteFolder+"/js/functions.js", "w")
            jsfunctions.write("$(function() { //page onload functions\n\n});")
            indexFile.write('    <script type="text/javascript" src="js/jquery.js"></script>\n    <script type="text/javascript" src="js/functions.js"></script>')
        
        if self.cssBox.isChecked():
            cssFile = open(siteFolder+"/style.css", "w")
            cssFile.write('body {\n    margin: 0 auto;\n}')
            indexFile.write('\n    <link rel="stylesheet" type="text/css" href="style.css" />')
        
        indexFile.write('\n</head>\n\n<body>\n')
        

    def __tr(self,s,c = None):
        return qApp.translate("NewSite",s,c)

if __name__ == "__main__":
    app = QApplication(sys.argv)
    f = NewSite()
    f.show()
    app.setMainWidget(f)
    app.exec_loop()

```

---

### Post by lapubell on 2009-03-09
now that it's modnay, any ideas?

---

### Post by ajackson on 2009-03-09
Well I have PyQT4 installed and the documentation is held in
```
/usr/share/doc/python-qt4-doc
```
So I'd assume for PyQT3 there will be a similar directory, inside that is a html directory with various references pages.

In the same base directory is an examples directory, failing that the function names and how to use them should (hopefully) be identical to C++ examples you have already found.

---

