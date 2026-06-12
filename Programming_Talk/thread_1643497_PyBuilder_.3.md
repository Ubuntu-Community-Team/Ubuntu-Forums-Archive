---
title: "PyBuilder .3"
date: 2010-12-12
forum: Programming Talk
---

### Post by JeremiahS on 2010-12-12
Hi. This is my second time using PyBuilder to make Windows Executables. My first time worked out great, but with my new program this is all I get...

cd C:/Documents and Settings/Main/Desktop/Projects/Python/Advanced Caesarian Cypher/Version 1.0/Py
Checking files ...
Copying Files to build\...
Making Setup.pyw ...
Copying script ...
copy "ACC.py" "build\a.py"
1 file(s) copied.
start setup.pyw py2exe -d "C:\Documents and Settings\Main\Desktop\Projects\Python\Advanced Caesarian Cypher\Version 1.0\Py\Binary"

running py2exe
creating C:\Documents and Settings\Main\Desktop\Projects\Python\Advanced Caesarian Cypher\Version 1.0\Py\build\build
creating C:\Documents and Settings\Main\Desktop\Projects\Python\Advanced Caesarian Cypher\Version 1.0\Py\build\build\bdist.win32
creating C:\Documents and Settings\Main\Desktop\Projects\Python\Advanced Caesarian Cypher\Version 1.0\Py\build\build\bdist.win32\winexe
creating C:\Documents and Settings\Main\Desktop\Projects\Python\Advanced Caesarian Cypher\Version 1.0\Py\build\build\bdist.win32\winexe\collect-2.6
creating C:\Documents and Settings\Main\Desktop\Projects\Python\Advanced Caesarian Cypher\Version 1.0\Py\build\build\bdist.win32\winexe\bundle-2.6
creating C:\Documents and Settings\Main\Desktop\Projects\Python\Advanced Caesarian Cypher\Version 1.0\Py\build\build\bdist.win32\winexe\temp
creating C:\Documents and Settings\Main\Desktop\Projects\Python\Advanced Caesarian Cypher\Version 1.0\Py\Binary

After this it just stops... Here is my code I'm trying to build... Maybe I'm not doing something...

```

#############################

#    Amnite Productions     #

# New Ideas To Old Problems #

# Advanced Caesarian Cypher #

#    Built On Python 2.6    #

#############################



import win32api

import sys

from UserString import MutableString

from Tkinter import Tk



win32api.SetConsoleTitle('Advanced Caesarian Cypher - Amnite Productions')



def GetMode():

    while True:

        print '\n(E)ncrypt Or (D)ecrypt?'

        Mode = raw_input().lower()

        if Mode in 'e d encrypt decrypt'.split():

            return Mode

        else:

            print '\nEnter Proper Choice!'



def GetInput():

    while True:

        print '\n(T)ype Message Or (L)oad File?'

        Input = raw_input().lower()

        if Input in 't type'.split():

            Input = raw_input()

            return Input

        elif Input in 'l load'.split():

            MsgLoc = raw_input()

            MsgLoc = open(MsgLoc, 'r')

            try:

                Input = MsgLoc.read()

                MsgLoc.close()

                return Input

            except:

                print '\nCould Not Open' , MsgLoc

        else:

            print '\nEnter Proper Choice!'



def GetKey():

    while True:

        Key = 0

        print '\nPlease Enter A 20 Digit Number...\n** Do NOT use zeros!!!! EX-NAY ERO-ZAY! **'

        try:

            Key = int(input())

            Key = str(Key)

            if (len(Key) == 20):

                return Key

            else:

                print('\nPlease Enter A Valid Number!')

        except:

            print('\nPlease Enter A Valid Number!')



def Translate(Mode, Input, Key):

    if Mode[0] == 'e':

        print('\nEncrypting....')

        Encrypt(Input, Key)

    else:

        print('\nDecrypting....')

        Decrypt(Input, Key)



def Encrypt(Input, Key):

    Msg = MutableString()

    NonMutMsg = Input

    Msg += NonMutMsg

    MsgLen = len(Msg)

    CypherKey = Key

    a = 0

    b = 19



    #Loop For Proccessing Key

    for z in range(10):

        KeySkip = int(CypherKey[a])

        KeyIncrement = int(CypherKey[b])

        c = MsgLen/KeySkip

        d = -1



        #Loop To Skip Then Increment

        for y in range(c):

            d = d+KeySkip

            LtrNum = ord(NonMutMsg[d])

            LtrNum = LtrNum + KeyIncrement

            Msg[d] = chr(LtrNum)



        a = a+1

        b = b-1



    #Tkinter Easiest Way To Copy

    e = Tk()

    e.withdraw()

    e.clipboard_clear()

    e.clipboard_append(Msg)

    e.destroy()



def Decrypt(Input, Key):

    Msg = MutableString()

    NonMutMsg = Input

    Msg += NonMutMsg

    MsgLen = len(Msg)

    CypherKey = Key

    a = 0

    b = 19



    #Loop For Proccessing Key

    for z in range(10):

        KeySkip = int(CypherKey[a])

        KeyIncrement = int(CypherKey[b])

        c = MsgLen/KeySkip

        d = -1



        #Loop To Skip Then Increment

        for y in range(c):

            d = d+KeySkip

            LtrNum = ord(NonMutMsg[d])

            LtrNum = LtrNum - KeyIncrement

            Msg[d] = chr(LtrNum)



        a = a+1

        b = b-1



    #Tkinter Easiest Way To Copy

    e = Tk()

    e.withdraw()

    e.clipboard_clear()

    e.clipboard_append(Msg)

    e.destroy()



Mode = GetMode()

Input = GetInput()

Key = GetKey()

Translate(Mode, Input, Key)



raw_input('Your Message Has Been Copied To The Clipboard... Press ENTER To Exit')

sys.exit(1)

```

---

