---
title: "Problems with Python Idle program"
date: 2016-02-16
forum: Packaging and Compiling Programs
---

### Post by James_Stinson on 2016-02-16
[COLOR=#333333][FONT=Helvetica]I am working with a combination of python idle 2.7.9 and adafruit lcd. I have made a program to act as a newspaper dispenser, in testing this I have come to a problem that I have been unable to fix. The adafruit lcd buttons are suppose to act as coins inserted. The left is a nickle, right button is a dime and down is a quarter. The object is to reach 30 cents to get the "door" to open and get a paper, at the end of this it is suppose to display the message " Enjoy your paper". The problem I am having is the buttons are not working and I need some help to figure out what I am doing wrong. The code is below and and help would be greatly appreciated.[/FONT][/COLOR]


from time import timefrom Adafruit_CharLCDPlate import Adafruit_CharLCDPlate


# Adafruit object


lcd = Adafruit_CharLCDPlate()


# declare the required variables


Inp_NICKEL = 5
Inp_DIME = 10
Inp_QUARTER = 25
tot = 0


# loop code to continuously process input


while (tot<30):


# code to represent switches on the Adafruit LCD


    lcd.message("Todays Paper\nOnly 30 Cents.")


if lcd.buttonPressed(lcd.LEFT):
    tot = tot + Inp_NICKEL
    print total()
    sleep(1)


if lcd.buttonPressed(lcd.RIGHT):
    tot = tot + Inp_DIME
    print total()
    sleep(1)


if lcd.buttonPressed(lcd.DOWN):
    tot = tot + Inp_QUARTER
    print total()
    sleep(1)


# Print the total and change when total equal to exact 30
if tot == 30:
    change = 0
    print total()
  
# Print the total and change when total is greater than 30  
if tot > 30:
    change = tot - 30
    print total()


DisplayMessage('Enjoy')
DisplayMessage('Your Paper')

---

