---
title: "probleme avec EditText(python-QT4)"
date: 2008-04-28
forum: Programming Talk
---

### Post by tsic on 2008-04-28
Bonjour,
je debute un code sur le chat entre un serveur et un client
En terminant l'interface à l'aide de QT4, et en l'executant à l'aide de Eric 4, j'ai trouvé que en copiant le contenu de lineEdit dans un EditText à l'aide d'un bouton envoyer celui ci ecrase le 1er texte envoyé et le remplace avec le text suivant.


LE probleme:
1)Je veux faire un retour à la ligne dans le EditText apres chaque envoie
2)Quand j'envoie queque chose comme "ç" il me genere une erreur (de code ascii)
Ma solution:
1)J'ai pensé à inserer dans le code "\n" mais ça n'a pas reussi

code:

 
```
def copier_txt(self): 
        ch=self.txt.text() 
        print "voila la chaine saisie: %s" % str(ch) 
        self.fenetre.setText(ch) 
        self.txt.clear() 

```


remarque:
txt: le nom du champs text(lineText)
fenetre: le nom du champs d'affichage(EditText)

C'est urgent
MERCI

---

### Post by tseliot on 2008-04-28
Can you write it in English, please?

**EDIT:** I don't speak French but it looks like you're having problems with French characters. Try using unicode and setting it to utf-8. Something like:

```
ch=self.txt.text() 
ch = unicode(ch, 'UTF-8')
print "voila la chaine saisie: %s" % str(ch)

```

---

### Post by tsic on 2008-04-28
Yes of corse,I'm sorry. So I said.

I begin with a chat python code between a server and a client
I excuted the interface (done with QT4) with ERIC 4. But I found that
when I write a text in my LineText end send it  to the EditText :every new text delete the previous one.

1)So, I want to know how can I modifiy my code to have every message
in a new line with EditText
2)Some times whene I send a text with for example "ç" it generates an
error (ascii) how can I correct that


Code python

```
def copier_txt(self):
       ch=self.txt.text()
       print "voila la chaine saisie: %s" % str(ch)
       self.fenetre.setText(ch)
       self.txt.clear()
```

=>
txt: is the name of my(lineText)
fenetre: is the name of my(EditText)

It's urgent
Thank you.

---

### Post by tseliot on 2008-04-28
Try this and see if it works:
[PHP]def copier_txt(self):
    ch = self.txt.text()
    ch = unicode(ch, 'UTF-8')
    print "voila la chaine saisie: %s" % ch
    self.fenetre.append(QString(ch))
    self.txt.clear()[/PHP]

EDIT: I'm sure that there's a more efficient way to do this by using only QStrings.

---

### Post by tsic on 2008-04-28
Thanks! it's ok for every message in a new line (I didn't put Qstring because it generates an error :"global name 'Qstring' is not defined")

But for the "ç,à,é......" it shows me this message:
" unhandled UnicodeDecodeError "'utf8' codec can't decode byte 0xe7 in position 0:unexpected end of data"

and the file "utf_8.py" apear in line 16:confused:

---

### Post by tseliot on 2008-04-28
> **tsic said:**
> Thanks! it's ok for every message in a new line (I didn't put Qstring because it generates an error :"global name 'Qstring' is not defined")
Put this at the beginning of your program:
[PHP]from PyQt4.QtCore import *
from PyQt4.QtGui import *[/PHP]

Then you will be able to use QStrings (which you should use).

---

### Post by tsic on 2008-04-28
OK,it works but the error of "ç,à,é......" still:
" unhandled UnicodeDecodeError "'utf8' codec can't decode byte 0xe7 in position 0:unexpected end of data"

and the file "utf_8.py" apear in line 16

Other thing how can I put the cursor automatically in the lineText after sending the message.
thank you

---

### Post by tseliot on 2008-04-28
Can you upload the source code somewhere (pastebin would be ok) so that I can try it here?

---

### Post by tseliot on 2008-04-28
> **tsic said:**
> Other thing how can I put the cursor automatically in the lineText after sending the message.
thank you
You should read the class reference:
[http://www.riverbankcomputing.com/static/Docs/PyQt4/html/qtextcursor.html](http://www.riverbankcomputing.com/static/Docs/PyQt4/html/qtextcursor.html)

---

### Post by tsic on 2008-04-28
```

# -*- coding: utf-8 -*-

# Form implementation generated from reading ui file 'f_chat2.ui'
#
# Created: Mon Apr 28 10:29:07 2008
#      by: PyQt4 UI code generator 4.3.3
#
# WARNING! All changes made in this file will be lost!
import sys
from PyQt4 import QtCore, QtGui
from PyQt4.QtCore import * 
from PyQt4.QtGui import *  

class Ui_Form(object):
    def setupUi(self, Form):
        Form.setObjectName("Form")
        Form.resize(QtCore.QSize(QtCore.QRect(0,0,478,395).size()).expandedTo(Form.minimumSizeHint()))

        self.button_envoyer = QtGui.QPushButton(Form)
        self.button_envoyer.setGeometry(QtCore.QRect(350,310,101,31))
        self.button_envoyer.setObjectName("button_envoyer")

        self.txt = QtGui.QLineEdit(Form)
        self.txt.setGeometry(QtCore.QRect(20,310,321,31))
        self.txt.setObjectName("txt")

        self.fenetre = QtGui.QTextEdit(Form)
        self.fenetre.setGeometry(QtCore.QRect(20,30,321,261))
        self.fenetre.setObjectName("fenetre")

        self.retranslateUi(Form)
        QtCore.QObject.connect(self.button_envoyer,QtCore.SIGNAL("clicked()"),self.copier_txt)
        QtCore.QMetaObject.connectSlotsByName(Form)

    def retranslateUi(self, Form):
        Form.setWindowTitle(QtGui.QApplication.translate("Form", "Form", None, QtGui.QApplication.UnicodeUTF8))
        self.button_envoyer.setText(QtGui.QApplication.translate("Form", "envoyer", None, QtGui.QApplication.UnicodeUTF8))

    def copier_txt(self): 
        ch = self.txt.text() 
        ch = unicode(ch, 'UTF-8') 
        self.fenetre.setText("C>")
        self.fenetre.append(QString(ch)) 
        self.txt.clear()  

        
if __name__ == "__main__":
    app = QtGui.QApplication(sys.argv)
    Form = QtGui.QMainWindow()
    ui = Ui_Form()
    ui.setupUi(Form)
    Form.show()
    sys.exit(app.exec_())



```


Please,I want also that when I type "Enter" it send the message like in messenger and the cursor return automatically in textLine after sending.

Thank youuuuuuu.

---

### Post by tseliot on 2008-04-28
This code works well with ààèè and other characters:
[PHP]def copier_txt(self): 
        ch = self.txt.text()
        self.fenetre.append("C>")
        self.fenetre.append(ch) 
        self.txt.clear()[/PHP]

---

### Post by tsic on 2008-04-28
:KS
yes it works
thank uu =D>

---

