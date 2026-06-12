---
title: "Python QSysTrayIcon Module Locking up computer"
date: 2008-04-01
forum: Programming Talk
---

### Post by xelapond on 2008-04-01
Hello, 

I started writing a module for my program to draw an Icon in the system tray.  I am basing it on the example provided in the current PyQt snapshot, because I cannot find ANY documentation as far as using it in python.  It is nowhere near finished, as I am having trouble getting it to actually display an icon(it wants some sort of QString, apparently a python string isn't good enough).  I could have very well finished it by now, but every time I run it the computer locks up.  The ONLY thing that works is moving the cursor, can't click anything, can reset X-Server, cant do anything.  So I have to hard reset my computer every time I try the program.  Before it locks up, though, it makes a spot for the icon in the tray and has a menu that I can open, I just don't know how to set an icon.  Can you help me figure out why it keeps doing this?  I think it started doing this when I started using the QString, did I define that correctly?


Here is the code:
[PHP]#!/usr/bin/env python

import sys
from PyQt4 import QtGui, QtCore

class Window(QtGui.QWidget):
    def __init__(self):
        QtGui.QWidget.__init__(self)

        self.createActions()
        self.createTrayIcon()

        QtCore.QObject.connect(self.trayIcon,
                QtCore.SIGNAL("messageClicked()"), self.messageClicked)
        #QtCore.QObject.connect(self.trayIcon,
          #      QtCore.SIGNAL("activated(QSystemTrayIcon::ActivationReason)"),
          #      self.iconActivated)

        self.trayIcon.show()
	self.create_tray_icon()

    #def setVisible(self, visible):
    #    QtGui.QWidget.setVisible(self, visible)

    def messageClicked(self):
        QtGui.QMessageBox.information(None, self.tr("Systray"),
                self.tr("Sorry, I already gave what help I could.\nMaybe you "
                    "should try asking a human?"))

    def createActions(self):
        self.quitAction = QtGui.QAction(self.tr("&Quit"), self)
        QtCore.QObject.connect(self.quitAction, QtCore.SIGNAL("triggered()"),
                QtGui.qApp, QtCore.SLOT("quit()"))

    def createTrayIcon(self):
         self.trayIconMenu = QtGui.QMenu(self)
         self.trayIconMenu.addAction(self.quitAction)
         self.trayIcon = QtGui.QSystemTrayIcon(self)
         self.trayIcon.setContextMenu(self.trayIconMenu)
	 
    def create_tray_icon(self):
	Filename = QtCore.QString()
        Filename = '/bad.png'
	Size = QtCore.QSize()
	Size.setHeight(176)
	Size.setWidth(156)
	self.trayIconPic = QtGui.QIcon(self)
	self.trayIconPic.addFile(self, Filename, Size, QIcon.Normal, QIcon.Off)


if __name__=='__main__':
    app = QtGui.QApplication(sys.argv)

    if not QtGui.QSystemTrayIcon.isSystemTrayAvailable():
        QtGui.QMessageBox.critical(None, QtCore.QObject.tr(app, "Systray"),
                QtCore.QObject.tr(app, "I couldn't detect any system tray on "
                    "this system."))
        sys.exit(1)

    window = Window()
    sys.exit(app.exec_())
[/PHP]

Thanks, 

Alex

---

