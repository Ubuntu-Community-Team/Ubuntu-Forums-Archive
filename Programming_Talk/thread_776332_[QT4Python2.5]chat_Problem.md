---
title: "[QT4/Python2.5]chat Problem"
date: 2008-04-30
forum: Programming Talk
---

### Post by tsic on 2008-04-30
My code server/multiclient functioned perfectly before I integred it into the interface QT4 but after,it's the total disaster. I was obliged to eliminate the thread and to put a simple client code and dispite:the interface QT4 (of server which I made) containing a editText and lineText a button to send: allowing the transfer of data between a server and many clients(executed by DOS). The program is realized with python2.5.
And not C++!!!!


The problem is when I execute the program the interface blocks (after I press on the button connection). I tryed to modify but I didn't find the solution.

the is my Server Code:
```

def chat(self):
       
        rep = self.chates.text()
        self.envoies.append("Donnees Envoyees>"+rep)     
        self.chates.clear()             
        return rep
     
    def conec(self):
        HOST = self.adripes.text()
        PORT = int(self.nipes.text())
       
        mySocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
       
        try:
            mySocket.bind((HOST, PORT))
        except socket.error:
            self.envoies.setText("La liaison du socket a l'adresse choisie a echoue.")
            sys.exit()
        while 1:
            self.envoies.append("Serveur pret en attente de requetes .")
            mySocket.listen(5)   
            connexion, adresse = mySocket.accept()
            c= time.strftime('%A %c')
            client= "Connexion au port" + str(adresse[1]) + "  a " + c
            self.envoies.append(client)
            donneesRecues = connexion.recv(8192)
            t=time.strftime("%H:%M:%S")
            self.envoies.append(" Donnees Recues " +t+ " > "+ donneesRecues)
            rep = self.chat()
            connexion.send(rep)

```

when I searched in the internet I found some of Qthread...
I didn't understand how to use them or what are their utilities.

thank u

---

### Post by tseliot on 2008-05-01
Can I see the full code so that I can test it here?

---

### Post by tsic on 2008-05-01
ok
This is my interface + server Code:
```

# -*- coding: utf-8 -*-

# Form implementation generated from reading ui file 'interf_s.ui'
#
# Created: Tue Apr 29 12:55:58 2008
#      by: PyQt4 UI code generator 4.3.3
#
# WARNING! All changes made in this file will be lost!

from PyQt4 import QtCore, QtGui
import socket, sys, threading
import time
import locale

class Ui_MainWindow(object):
    def setupUi(self, MainWindow):
        MainWindow.setObjectName("MainWindow")
        MainWindow.resize(QtCore.QSize(QtCore.QRect(0,0,610,600).size()).expandedTo(MainWindow.minimumSizeHint()))

        self.centralwidget = QtGui.QWidget(MainWindow)
        self.centralwidget.setObjectName("centralwidget")

        self.gc = QtGui.QGroupBox(self.centralwidget)
        self.gc.setGeometry(QtCore.QRect(9,9,581,111))
        self.gc.setObjectName("gc")

        self.adripes = QtGui.QLineEdit(self.gc)
        self.adripes.setGeometry(QtCore.QRect(110,30,301,20))
        self.adripes.setObjectName("adripes")

        self.label = QtGui.QLabel(self.gc)
        self.label.setGeometry(QtCore.QRect(20,30,71,16))
        self.label.setObjectName("label")

        self.label_2 = QtGui.QLabel(self.gc)
        self.label_2.setGeometry(QtCore.QRect(20,60,91,16))
        self.label_2.setObjectName("label_2")

        self.nipes = QtGui.QLineEdit(self.gc)
        self.nipes.setGeometry(QtCore.QRect(110,60,301,20))
        self.nipes.setObjectName("nipes")

        self.connectes = QtGui.QPushButton(self.gc)
        self.connectes.setGeometry(QtCore.QRect(470,70,91,23))
        self.connectes.setObjectName("connectes")

        self.envoies = QtGui.QTextEdit(self.centralwidget)
        self.envoies.setGeometry(QtCore.QRect(10,150,256,271))
        self.envoies.setObjectName("envoies")

        self.chates = QtGui.QLineEdit(self.centralwidget)
        self.chates.setGeometry(QtCore.QRect(10,450,256,31))
        self.chates.setObjectName("chates")

        self.benves = QtGui.QPushButton(self.centralwidget)
        self.benves.setGeometry(QtCore.QRect(190,520,75,23))
        self.benves.setObjectName("benves")

        self.gt = QtGui.QGroupBox(self.centralwidget)
        self.gt.setGeometry(QtCore.QRect(280,140,311,401))
        self.gt.setObjectName("gt")

        self.tablees = QtGui.QTableWidget(self.gt)
        self.tablees.setGeometry(QtCore.QRect(20,40,281,181))
        self.tablees.setObjectName("tablees")

        self.ajoues = QtGui.QPushButton(self.gt)
        self.ajoues.setGeometry(QtCore.QRect(210,280,75,23))
        self.ajoues.setObjectName("ajoues")

        self.suppes = QtGui.QPushButton(self.gt)
        self.suppes.setGeometry(QtCore.QRect(210,330,75,23))
        self.suppes.setObjectName("suppes")
        MainWindow.setCentralWidget(self.centralwidget)

        self.statusbar = QtGui.QStatusBar(MainWindow)
        self.statusbar.setObjectName("statusbar")
        MainWindow.setStatusBar(self.statusbar)

        self.menubar = QtGui.QMenuBar(MainWindow)
        self.menubar.setGeometry(QtCore.QRect(0,0,610,21))
        self.menubar.setObjectName("menubar")
        MainWindow.setMenuBar(self.menubar)

        self.retranslateUi(MainWindow)
        QtCore.QObject.connect(self.ajoues,QtCore.SIGNAL("clicked()"),self.ajout)
        QtCore.QObject.connect(self.suppes,QtCore.SIGNAL("clicked()"),self.supprim)
        QtCore.QObject.connect(self.connectes,QtCore.SIGNAL("clicked()"),self.conec)
        QtCore.QObject.connect(self.benves,QtCore.SIGNAL("clicked()"),self.chat)
        QtCore.QMetaObject.connectSlotsByName(MainWindow)

    def retranslateUi(self, MainWindow):
        MainWindow.setWindowTitle(QtGui.QApplication.translate("MainWindow", "MainWindow", None, QtGui.QApplication.UnicodeUTF8))
        self.gc.setTitle(QtGui.QApplication.translate("MainWindow", "Connexion :", None, QtGui.QApplication.UnicodeUTF8))
        self.label.setText(QtGui.QApplication.translate("MainWindow", "Adresse IP :", None, QtGui.QApplication.UnicodeUTF8))
        self.label_2.setText(QtGui.QApplication.translate("MainWindow", "Numero de port  :", None, QtGui.QApplication.UnicodeUTF8))
        self.connectes.setText(QtGui.QApplication.translate("MainWindow", "Connexion", None, QtGui.QApplication.UnicodeUTF8))
        self.envoies.setHtml(QtGui.QApplication.translate("MainWindow", "<html><head><meta name=\"qrichtext\" content=\"1\" /><style type=\"text/css\">\n"
        "p, li { white-space: pre-wrap; }\n"
        "</style></head><body style=\" font-family:\'MS Shell Dlg 2\'; font-size:8.25pt; font-weight:400; font-style:normal;\">\n"
        "<p style=\"-qt-paragraph-type:empty; margin-top:0px; margin-bottom:0px; margin-left:0px; margin-right:0px; -qt-block-indent:0; text-indent:0px; font-size:8pt;\"></p></body></html>", None, QtGui.QApplication.UnicodeUTF8))
        self.benves.setText(QtGui.QApplication.translate("MainWindow", "Envoyer", None, QtGui.QApplication.UnicodeUTF8))
        self.gt.setTitle(QtGui.QApplication.translate("MainWindow", "Gestion commandes :", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.clear()
        self.tablees.setColumnCount(2)
        self.tablees.setRowCount(3)

        headerItem = QtGui.QTableWidgetItem()
        headerItem.setText(QtGui.QApplication.translate("MainWindow", "Commande 1", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setVerticalHeaderItem(0,headerItem)

        headerItem1 = QtGui.QTableWidgetItem()
        headerItem1.setText(QtGui.QApplication.translate("MainWindow", "Commande 2", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setVerticalHeaderItem(1,headerItem1)

        headerItem2 = QtGui.QTableWidgetItem()
        headerItem2.setText(QtGui.QApplication.translate("MainWindow", "Commande 3", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setVerticalHeaderItem(2,headerItem2)

        headerItem3 = QtGui.QTableWidgetItem()
        headerItem3.setText(QtGui.QApplication.translate("MainWindow", "Requête", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setHorizontalHeaderItem(0,headerItem3)

        headerItem4 = QtGui.QTableWidgetItem()
        headerItem4.setText(QtGui.QApplication.translate("MainWindow", "Reponse", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setHorizontalHeaderItem(1,headerItem4)

        item = QtGui.QTableWidgetItem()
        item.setText(QtGui.QApplication.translate("MainWindow", "$ GPSCON", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setItem(0,0,item)

        item1 = QtGui.QTableWidgetItem()
        item1.setText(QtGui.QApplication.translate("MainWindow", "Bonjour", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setItem(0,1,item1)

        item2 = QtGui.QTableWidgetItem()
        item2.setText(QtGui.QApplication.translate("MainWindow", "$ GPSNMUN", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setItem(1,0,item2)

        item3 = QtGui.QTableWidgetItem()
        item3.setText(QtGui.QApplication.translate("MainWindow", "OK", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setItem(1,1,item3)

        item4 = QtGui.QTableWidgetItem()
        item4.setText(QtGui.QApplication.translate("MainWindow", "$ GPSACP", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setItem(2,0,item4)

        item5 = QtGui.QTableWidgetItem()
        item5.setText(QtGui.QApplication.translate("MainWindow", "Hello", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setItem(2,1,item5)
        self.ajoues.setText(QtGui.QApplication.translate("MainWindow", "Ajouter", None, QtGui.QApplication.UnicodeUTF8))
        self.suppes.setText(QtGui.QApplication.translate("MainWindow", "Supprimer", None, QtGui.QApplication.UnicodeUTF8))

    def ajout(self):
        self.tablees.insertRow(3)
    
    def supprim(self):
        self.tablees.removeRow(3)
    
    def chat(self):
        
        rep = self.chates.text() 
        self.envoies.append("Donnees Envoyees>"+rep)      
        self.chates.clear()              
        return rep
        #self.envoies.append("Deconnexion de ", self.client_address)


    
    def conec(self):
        HOST = self.adripes.text()
        PORT = int(self.nipes.text())
        
        mySocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        
        try:
            mySocket.bind((HOST, PORT))
        except socket.error:
            self.envoies.setText("La liaison du socket a l'adresse choisie a echoue.")
            sys.exit()
        while 1:
            self.envoies.append("Serveur pret en attente de requetes .")
            mySocket.listen(5)   
            connexion, adresse = mySocket.accept()
            c= time.strftime('%A %c')
            client= "Connexion au port" + str(adresse[1]) + "  a " + c
            self.envoies.append(client)
            donneesRecues = connexion.recv(8192)
            t=time.strftime("%H:%M:%S")
            self.envoies.append(" Donnees Recues " +t+ " > "+ donneesRecues)
            rep = self.chat() 
            connexion.send(rep)


if __name__ == "__main__":
    import sys
    app = QtGui.QApplication(sys.argv)
    MainWindow = QtGui.QMainWindow()
    ui = Ui_MainWindow()
    ui.setupUi(MainWindow)
    MainWindow.show()
    sys.exit(app.exec_())


```

Notice: if I remove While in def conec(self), the transfer of data works for the first time from client to the TextEdit and don't work from interface server to the client and then the socket close the connection

My client should be able to send many message this is his code:

```

# Definition d"un client reseau gerant en parallele l'emission
# et la reception des messages (utilisation de 2 THREADS).

host = '127.0.0.1'
port = 84

import socket, sys, threading

class ThreadReception(threading.Thread):
    """objet thread gerant la reception des messages"""
    def __init__(self, conn):
        threading.Thread.__init__(self)
        self.connexion = conn           # ref. du socket de connexion
        
    def run(self):
        while 1:
            message_recu = self.connexion.recv(1024)
            print "Donnees Recues>" + message_recu 
            
        # Le thread <reception> se termine ici.
        # On force la fermeture du thread <emission> :

        print "Client arrete. Connexion interrompue."
        self.connexion.close()
    
class ThreadEmission(threading.Thread):
    
    """objet thread gerant l'emission des messages"""
    def __init__(self, conn):
        threading.Thread.__init__(self)
        self.connexion = conn           # ref. du socket de connexion
        
    def run(self):
        message_final=""
        while 1:
            message_final=""
            message_emis = raw_input("C> \n")
            message_final = message_final + " \n "+ message_emis
            self.connexion.send(message_final)




# Programme principal - etablissement de la connexion :
connexion = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
try:
    connexion.connect((host, port))
except socket.error:
    print "La connexion a echoue."
    sys.exit()    
print "Connexion etablie avec le serveur."
            
# Dialogue avec le serveur : on lance deux threads pour gerer
# independamment l'emission et la reception des messages :

th_E = ThreadEmission(connexion)
th_R = ThreadReception(connexion)
th_E.start()
th_R.start()       



```

Notice:
This client enter into an infinite buckle when I try to send a message from it to the interface So I was obliged to work with a simple client code . But this is not the solution that I want:

```

# Definition d_un client reseau rudimentaire
# Ce client dialogue avec un serveur ad hoc

import socket, sys

HOST = '127.0.0.1'
PORT = 84

# 1) creation du socket :
mySocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# 2) envoi d_une requete de connexion au serveur :
try:
    mySocket.connect((HOST, PORT))
except socket.error:
    print "La connexion a echoue."
    sys.exit()    
print "Connexion etablie avec le serveur."    

# 3) Dialogue avec le serveur :


while 1:
    msgClient = raw_input("C> ")
    mySocket.send(msgClient)
    msgServeur = mySocket.recv(1024)
    print "S>", msgServeur 
# 4) Fermeture de la connexion :
print "Connexion interrompue."
mySocket.close()


```


Thank you a lot .

---

### Post by tseliot on 2008-05-01
I'm not an expert in networks and I haven't studied multi-threading with QT4 yet, however I came up with this solution which at least doesn't block the interface.

I warmly recommend you to buy [this book]("http://www.amazon.co.uk/Rapid-GUI-Programming-Python-Development/dp/0132354187/ref=pd_sxp_grid_pt_1_1") and to read chapter 19, which should contain everything you need. This book is a must-have if you use PyQT4.

Here's the code (**NOTE: this code might suck**):
[PHP]# -*- coding: utf-8 -*-

# Form implementation generated from reading ui file 'interf_s.ui'
#
# Created: Tue Apr 29 12:55:58 2008
#      by: PyQt4 UI code generator 4.3.3
#
# WARNING! All changes made in this file will be lost!

from PyQt4 import QtCore, QtGui
from PyQt4.QtCore import *
from PyQt4.QtGui import *
import socket, sys, threading
import time
import locale

class Thread(QThread):
    #lock = QReadWriteLock()
    def __init__(self, host, port):
        super(Thread, self).__init__()
        #self.socketId = socketId
        self.host = host
        self.port = port
    
    def run(self):
        HOST = self.host
        PORT = int(self.port)
        
        mySocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        
        try:
            mySocket.bind((HOST, PORT))
        except socket.error:
            #self.envoies.setText("La liaison du socket a l'adresse choisie a echoue.")
            print "La liaison du socket a l'adresse choisie a echoue."
            sys.exit()
        while 1:
            #self.envoies.append("Serveur pret en attente de requetes .")
            print "Serveur pret en attente de requetes ."
            mySocket.listen(5)   
            connexion, adresse = mySocket.accept()
            c= time.strftime('%A %c')
            client= "Connexion au port" + str(adresse[1]) + "  a " + c
            #self.envoies.append(client)
            print client
            donneesRecues = connexion.recv(8192)
            t=time.strftime("%H:%M:%S")
            #self.envoies.append(" Donnees Recues " +t+ " > "+ donneesRecues)
            rep = " Donnees Recues " +t+ " > "+ donneesRecues
            print rep
            #rep = self.chat() 
            connexion.send(rep)
            
            #"Donnees Envoyees>"+rep

class Ui_MainWindow(object):
    def setupUi(self, MainWindow):
        MainWindow.setObjectName("MainWindow")
        MainWindow.resize(QtCore.QSize(QtCore.QRect(0,0,610,600).size()).expandedTo(MainWindow.minimumSizeHint()))

        self.centralwidget = QtGui.QWidget(MainWindow)
        self.centralwidget.setObjectName("centralwidget")

        self.gc = QtGui.QGroupBox(self.centralwidget)
        self.gc.setGeometry(QtCore.QRect(9,9,581,111))
        self.gc.setObjectName("gc")

        self.adripes = QtGui.QLineEdit(self.gc)
        self.adripes.setGeometry(QtCore.QRect(110,30,301,20))
        self.adripes.setObjectName("adripes")

        self.label = QtGui.QLabel(self.gc)
        self.label.setGeometry(QtCore.QRect(20,30,71,16))
        self.label.setObjectName("label")

        self.label_2 = QtGui.QLabel(self.gc)
        self.label_2.setGeometry(QtCore.QRect(20,60,91,16))
        self.label_2.setObjectName("label_2")

        self.nipes = QtGui.QLineEdit(self.gc)
        self.nipes.setGeometry(QtCore.QRect(110,60,301,20))
        self.nipes.setObjectName("nipes")

        self.connectes = QtGui.QPushButton(self.gc)
        self.connectes.setGeometry(QtCore.QRect(470,70,91,23))
        self.connectes.setObjectName("connectes")

        self.envoies = QtGui.QTextEdit(self.centralwidget)
        self.envoies.setGeometry(QtCore.QRect(10,150,256,271))
        self.envoies.setObjectName("envoies")

        self.chates = QtGui.QLineEdit(self.centralwidget)
        self.chates.setGeometry(QtCore.QRect(10,450,256,31))
        self.chates.setObjectName("chates")

        self.benves = QtGui.QPushButton(self.centralwidget)
        self.benves.setGeometry(QtCore.QRect(190,520,75,23))
        self.benves.setObjectName("benves")

        self.gt = QtGui.QGroupBox(self.centralwidget)
        self.gt.setGeometry(QtCore.QRect(280,140,311,401))
        self.gt.setObjectName("gt")

        self.tablees = QtGui.QTableWidget(self.gt)
        self.tablees.setGeometry(QtCore.QRect(20,40,281,181))
        self.tablees.setObjectName("tablees")

        self.ajoues = QtGui.QPushButton(self.gt)
        self.ajoues.setGeometry(QtCore.QRect(210,280,75,23))
        self.ajoues.setObjectName("ajoues")

        self.suppes = QtGui.QPushButton(self.gt)
        self.suppes.setGeometry(QtCore.QRect(210,330,75,23))
        self.suppes.setObjectName("suppes")
        MainWindow.setCentralWidget(self.centralwidget)

        self.statusbar = QtGui.QStatusBar(MainWindow)
        self.statusbar.setObjectName("statusbar")
        MainWindow.setStatusBar(self.statusbar)

        self.menubar = QtGui.QMenuBar(MainWindow)
        self.menubar.setGeometry(QtCore.QRect(0,0,610,21))
        self.menubar.setObjectName("menubar")
        MainWindow.setMenuBar(self.menubar)

        self.retranslateUi(MainWindow)
        QtCore.QObject.connect(self.ajoues,QtCore.SIGNAL("clicked()"),self.ajout)
        QtCore.QObject.connect(self.suppes,QtCore.SIGNAL("clicked()"),self.supprim)
        QtCore.QObject.connect(self.connectes,QtCore.SIGNAL("clicked()"),self.conec)
        QtCore.QObject.connect(self.benves,QtCore.SIGNAL("clicked()"),self.chat)
        QtCore.QMetaObject.connectSlotsByName(MainWindow)

    def retranslateUi(self, MainWindow):
        MainWindow.setWindowTitle(QtGui.QApplication.translate("MainWindow", "MainWindow", None, QtGui.QApplication.UnicodeUTF8))
        self.gc.setTitle(QtGui.QApplication.translate("MainWindow", "Connexion :", None, QtGui.QApplication.UnicodeUTF8))
        self.label.setText(QtGui.QApplication.translate("MainWindow", "Adresse IP :", None, QtGui.QApplication.UnicodeUTF8))
        self.label_2.setText(QtGui.QApplication.translate("MainWindow", "Numero de port  :", None, QtGui.QApplication.UnicodeUTF8))
        self.connectes.setText(QtGui.QApplication.translate("MainWindow", "Connexion", None, QtGui.QApplication.UnicodeUTF8))
        self.envoies.setHtml(QtGui.QApplication.translate("MainWindow", "<html><head><meta name=\"qrichtext\" content=\"1\" /><style type=\"text/css\">\n"
        "p, li { white-space: pre-wrap; }\n"
        "</style></head><body style=\" font-family:\'MS Shell Dlg 2\'; font-size:8.25pt; font-weight:400; font-style:normal;\">\n"
        "<p style=\"-qt-paragraph-type:empty; margin-top:0px; margin-bottom:0px; margin-left:0px; margin-right:0px; -qt-block-indent:0; text-indent:0px; font-size:8pt;\"></p></body></html>", None, QtGui.QApplication.UnicodeUTF8))
        self.benves.setText(QtGui.QApplication.translate("MainWindow", "Envoyer", None, QtGui.QApplication.UnicodeUTF8))
        self.gt.setTitle(QtGui.QApplication.translate("MainWindow", "Gestion commandes :", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.clear()
        self.tablees.setColumnCount(2)
        self.tablees.setRowCount(3)

        headerItem = QtGui.QTableWidgetItem()
        headerItem.setText(QtGui.QApplication.translate("MainWindow", "Commande 1", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setVerticalHeaderItem(0,headerItem)

        headerItem1 = QtGui.QTableWidgetItem()
        headerItem1.setText(QtGui.QApplication.translate("MainWindow", "Commande 2", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setVerticalHeaderItem(1,headerItem1)

        headerItem2 = QtGui.QTableWidgetItem()
        headerItem2.setText(QtGui.QApplication.translate("MainWindow", "Commande 3", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setVerticalHeaderItem(2,headerItem2)

        headerItem3 = QtGui.QTableWidgetItem()
        headerItem3.setText(QtGui.QApplication.translate("MainWindow", "Requête", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setHorizontalHeaderItem(0,headerItem3)

        headerItem4 = QtGui.QTableWidgetItem()
        headerItem4.setText(QtGui.QApplication.translate("MainWindow", "Reponse", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setHorizontalHeaderItem(1,headerItem4)

        item = QtGui.QTableWidgetItem()
        item.setText(QtGui.QApplication.translate("MainWindow", "$ GPSCON", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setItem(0,0,item)

        item1 = QtGui.QTableWidgetItem()
        item1.setText(QtGui.QApplication.translate("MainWindow", "Bonjour", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setItem(0,1,item1)

        item2 = QtGui.QTableWidgetItem()
        item2.setText(QtGui.QApplication.translate("MainWindow", "$ GPSNMUN", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setItem(1,0,item2)

        item3 = QtGui.QTableWidgetItem()
        item3.setText(QtGui.QApplication.translate("MainWindow", "OK", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setItem(1,1,item3)

        item4 = QtGui.QTableWidgetItem()
        item4.setText(QtGui.QApplication.translate("MainWindow", "$ GPSACP", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setItem(2,0,item4)

        item5 = QtGui.QTableWidgetItem()
        item5.setText(QtGui.QApplication.translate("MainWindow", "Hello", None, QtGui.QApplication.UnicodeUTF8))
        self.tablees.setItem(2,1,item5)
        self.ajoues.setText(QtGui.QApplication.translate("MainWindow", "Ajouter", None, QtGui.QApplication.UnicodeUTF8))
        self.suppes.setText(QtGui.QApplication.translate("MainWindow", "Supprimer", None, QtGui.QApplication.UnicodeUTF8))

    def ajout(self):
        self.tablees.insertRow(3)
    
    def supprim(self):
        self.tablees.removeRow(3)
    
    def chat(self):
        
        rep = self.chates.text() 
        self.envoies.append("Donnees Envoyees>"+rep)      
        self.chates.clear()              
        return rep
        #self.envoies.append("Deconnexion de ", self.client_address)


    
    def conec(self):
        HOST = self.adripes.text()
        PORT = int(self.nipes.text())
        thread = Thread(HOST, PORT)
        QtCore.QObject.connect(thread, SIGNAL("finished()"),
                     thread, SLOT("deleteLater()"))
        thread.start()
        


if __name__ == "__main__":
    import sys
    app = QtGui.QApplication(sys.argv)
    MainWindow = QtGui.QMainWindow()
    ui = Ui_MainWindow()
    ui.setupUi(MainWindow)
    MainWindow.show()
    sys.exit(app.exec_())[/PHP]

---

### Post by tsic on 2008-05-01
It seems that is a better solution but when I tried it, when I clicked on button_connection , a debugue meesage apear:


pythonw.exe encountered a problem and must close. Excuse us for the incurred ....

Is the program works with you?
May be I have something missing..

---

### Post by tseliot on 2008-05-01
This is what happens here:
[http://albertomilone.com/client.png](http://albertomilone.com/client.png)

---

### Post by tseliot on 2008-05-01
You're using Windows. Can you launch the program from a terminal (MsDos prompt) so that we can get a helpful error message?

---

### Post by tsic on 2008-05-01
Hello,
in your picture.png the first line in DOS is: "loading simple config module..."
But in mine the is just one line : "QThread:Destroyed while thread is still running" with the appearance of the error message interface "python.exe encountered a problem and must close..."

---

### Post by tseliot on 2008-05-01
Can you try the .pyw file instead of converting it into a .exe?
You will have to launch it (more or less) in this way:
C:\\path_to_python\python.exe name_of_the_program.pyw

---

### Post by tsic on 2008-05-01
I'm really sorry!
But it doesn't work:cry:
1)I tried to save the file as my_interface.pyw
and executed it in DOS
the same error message appear
2)I tried to execute my_interface.py from python.exe file
the result:
Taceback <most recent call last>:
   File"<stdin>";line1,in <module>
NameError:name...is not defined


:-k:confused:
I don't know what to do
may be there is a module missing?!!

---

### Post by tseliot on 2008-05-01
Try asking here:
[http://www.nabble.com/PyQt-f23444.html](http://www.nabble.com/PyQt-f23444.html)

---

### Post by tsic on 2008-05-22
Hello tseliot,
Could you please write the full code of the server that you used to try the connection with this client recently posted that I can try it again. May be the fault is of my server.
Thank you

---

