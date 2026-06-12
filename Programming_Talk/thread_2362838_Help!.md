---
title: "Help!"
date: 2017-06-02
forum: Programming Talk
---

### Post by shotingman03 on 2017-06-02
[I][B]Please help!
[/B][/I]t don't know what the problem is but here is my code:
# Namn: Dåliga saker händer...
# Beskrivning: Ett textbaserat spel där man hamnar i dåliga miljöer...


import random
import time


def displayIntro():
    print()
    print("--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------")
    print( "Namn: Dåliga saker händer...")
    print("Beskrivning: Ett textbaserat spel där man hamnar i dåliga miljöer...")
    print("Detta spel är under Copyright license.")
    print("Man får använda spelet om man har tillåtelse av utveckaren.")
    print()
    print("---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------")
    print("Efter flera år med en massa krig med en massa rymdvarelser, så är du på väg hem till jorden.")
    print("Nu kommer du till en korsning, där en väg leder hem, till jorden")
    print("(där kommer du att bi riktigt belönad).")
    print("Den andra leder igenom en supernova.")
    print()


def choosePath(): 
    path = ""
    while path != "1" and path != "2": # Input validation 1
        path = input("Vilken väg väljer du, (1 eller 2). För att göra val i det här spelet så skriver du vad du väljer.")


    return path


def checkPath(chosenPath):
    print("Du flyger ovanför vägen..")
    time.sleep(2)
    print("Det är en astroid som ser bekant ut, det måste vara ett bra tecken...")
    time.sleep(2)
    print("Ditt skinn börjar att stickas...")
    print()
    time.sleep(2)


    correctPath = random.randint(1, 2)


    if chosenPath == str(correctPath):
        print("Det stickningar kom bara ifrån en känsla av beundran från medborgarna i galaxen!")
        print("Välkomen hem, till jorden!")
        time.sleep(2)
        print()
        print("Du är väldigt nära jorden, där du ska få träffa alla större makter som kommer att säga tack till dig för ditt mycket bra ledarskap och för ditt kämpande.")
        print("Man har ett råd med 20 stycken ledare i världen som får styra hela jorden, men de måste göra det tillsammans.")
        time.sleep(2)
        print()
        print("Du landar nu på en platform där alla ledare står redo för att tacka dig. Det finns en massa vakter med fordon (vissa har drönare) och en massa civila också.")
        print("Du hör att vissa tackar dig redan.")
        print("Din farkost öppnar dörrarna nu.")
        print("Du går nu ut till alla.")
        time.sleep(5)
        print()
        print("      - Tack, säger en ledare och tar din hand.")
        time.sleep(2)
        print("      - Tack, säger en annan ledare och tar din hand.")
        time.sleep(2)
        print()
        print("Nu kommer det rymdvarelser och attackerar...")
        print("Du springer in i din farkost och börjar att skjuta. Nu ser du att en av ledarna inte hinner iväg till fordonet som de flög hit med och en rymdvarelse tar honom.")
        print("Du ser också att några andra rymdvarelser tar en massa civila.")
    else:
        print("En supernova spängde dig...")
        print("Detta fick alla atomer av dig och din rymdfarkost att bli istället till energi.")
        print("Nu finns det inga tecken på att du har funnits...")
        time.sleep(2)  
        print()
        print("---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------")


def chooseChoice(): 
    choice = ""
    while choice != "Civila" and choice != "Ledaren": # Input validation 2
        choice = input("Väljer du att rädda ledaren eller de civila?")


    return choice


    def checkChoice(chosenChoice):
        print("Plötsligt så fungerar inte din farkost...")
        time.sleep(2)
        print("Den sköts ned av någon form av EMP så att ingen elektronik fungerar...")
        time.sleep(2)
        print("Du tänker på hur du ska överleva kraschen...")
        time.sleep(2)
        print("Sedan så kommer du på att du har en fallskärm (du tar den) och hoppar ut ur farkosten...")
        time.sleep(2)
        print("Hade farkosten varit lite närmare marken så hade du dött..")
        time.sleep(2)
        print("Du kämpar fram på marken till dem...")
        print()


    if choosenChoice == str(Civila):
        print("Du räddade de civila från att dö och lät ledaren dö...")
        time.sleep(2)  
        print()
        print("---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------")
    else:
        print("Du räddade ledaren från att dö, men du lät de civila dö...")
        time.sleep(2)  
        print()
        print("---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------")


playAgain = "ja"
while playAgain == "ja" or playAgain == "j":
    displayIntro()
    choice = choosePath()
    checkPath(choice) # choice is equal to "1" or "2"
    playAgain = input ("Jag vet att spelet inte har bilder eller ljud, men det kommer! Vill du spela igen? I så fall skriv j.")

---

### Post by QIII on 2017-06-02
What is it that you want from us and when is the assignment due?

---

### Post by shotingman03 on 2017-06-02
I want everything to run like it should, but it doesn't.

---

### Post by QIII on 2017-06-02
And you expect the community to troubleshoot and debug the entire thing?

When do you have to turn this assignment in?

---

### Post by shotingman03 on 2017-06-02
I just want tips on what might be wrong.

---

### Post by QIII on 2017-06-02
What have you done to troubleshoot and debug your homework assignment?

---

