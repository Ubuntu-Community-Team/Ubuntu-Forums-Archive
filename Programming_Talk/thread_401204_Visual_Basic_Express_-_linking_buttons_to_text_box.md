---
title: "Visual Basic Express - linking buttons to text boxes"
date: 2007-04-04
forum: Programming Talk
---

### Post by renzokuken on 2007-04-04
Hi,

im hoping this a very easy thing to solve/explain. I am only just learning Visual Basic Express, since my supervisor wants me to try and write a program that calls on certain properties for a particular element.

Basically, i have a periodic table where each element is a button. when the element/button is clicked on, i want certain properties to be displayed in the text boxes at the bottom. obviously there are different properties for each element.

i have no idea where to input the values for each element and how to get them to appear in the text boxes below when the button is pressed.

any help would be really appreciated. i have enclosed a picture of my GUI so you can what i want to do.

cheers

Rob

---

### Post by kpatz on 2007-04-04
Have an OnClick event procedure on the button that fills in the text box values.

If your buttons are a control array (a good idea), you can use one event procedure for all the buttons.  Use a Select...Case statement or a pre-loaded array with the element's attributes to fill the text boxes when the button is clicked.

---

### Post by renzokuken on 2007-04-04
thanks for your reply kpatz.

sadly though i really dont have much of a clue what you mean. i'm learning as i go here.

i currently have the info displayed in a MsgBox when a button is clicked but i thought that was ugly and slow.

could you explain in more detail please.....thanks >_<

---

### Post by renzokuken on 2007-04-04
actually, i found out a way to do it.......its not ideal i know but its good enough for what i want. i just used

        TextBoxElement.Text = "Boron"
        TextBoxTemp.Text = "2000 C"
        TextBoxPressure.Text = "10 ^ -2"
        TextBoxSource.Text = "Knudsen Cell"
        TextBoxCrucible.Text = "steel"

etc for each button

---

### Post by kpatz on 2007-04-04
If you're displaying MsgBox when a button is clicked, then you have the event procedure already.  Are the buttons a control array, or not?  In other words, are they all named the same, with Index values in the properties, or are they all named differently?  A control array makes life a lot easier.

Anyway, let's say that your event procedure looks like this right now:```
Private Sub cmdElement_OnClick(Index as Integer)
  MsgBox "I clicked button " & Index
End Sub
```

To make it update the text boxes, change your MsgBox line to read (but change txtMyTextBox to whatever you named your text box):
```
txtMyTextBox.Text = "this is what I want to show in the text box"
```

If you used a control array, you'll have the Index parameter on your Sub.  You can use Index to determine which button in the array was clicked.```
Select Case Index
   Case 0: txtElementName.Text = "Hydrogen"
   Case 1: txtElementName.Text = "Helium"
    ... and so forth ...
End Select
```

---

### Post by kpatz on 2007-04-04
> **renzokuken said:**
> actually, i found out a way to do it.......its not ideal i know but its good enough for what i want. i just used

        TextBoxElement.Text = "Boron"
        TextBoxTemp.Text = "2000 C"
        TextBoxPressure.Text = "10 ^ -2"
        TextBoxSource.Text = "Knudsen Cell"
        TextBoxCrucible.Text = "steel"

etc for each buttonHere's a better way to do it.

First of all, make your buttons into a control array.  In other words, give them the same name but different Index values (this is easiest to do when copying/pasting the buttons).

Then, in the Declarations section of the code, add:```


Private ElementName() As String, ElementTemp() As String, ElementPressure() As String, _
   ElementSource()  As String, ElementCrucible() As String
```

In the Form_Load event, add:```

' This code assumes button array is named cmdButton, change as needed

ReDim ElementName(cmdButton.LBound to cmdButton.UBound)
ReDim ElementTemp(cmdButton.LBound to cmdButton.UBound)
ReDim ElementPressure(cmdButton.LBound to cmdButton.UBound)
ReDim ElementSource(cmdButton.LBound to cmdButton.UBound)
ReDim ElementCrucible(cmdButton.LBound to cmdButton.UBound)

' Assuming button 0 is hydrogen, 1 is helium, etc.

ElementName(0) = "Hydrogen"
ElementTemp(0) = "(hydrogen temperature here)"
ElementPressure(0) = "(hydrogen pressure here)"
ElementSource(0) = "(hydrogen source here)"
ElementCrucible(0) = "(hydrogen crucible here)"

ElementName(1) = "Helium"
ElementTemp(1) = "(helium temperature here)"
ElementPressure(1) = "(helium pressure here)"
ElementSource(1) = "(helium source here)"
ElementCrucible(1) = "(helium crucible here)"

  ... repeat for remaining elements ...
```

Then your OnClick event procedure would be:```
Private Sub cmdButton_Click(Index as Integer)
        TextBoxElement.Text = ElementName(Index)
        TextBoxTemp.Text = ElementTemp(Index)
        TextBoxPressure.Text = ElementPressure(Index)
        TextBoxSource.Text = ElementSource(Index)
        TextBoxCrucible.Text = ElementCrucible(Index)
End Sub
```

Your next exercise, should you choose to accept it, is to put the values into a text file, comma delimited, and load the file in the Load event, instead of having them hard coded:

```
"Boron","2000 C","10 ^ -2","Knudsen Cell","steel"
```

---

### Post by renzokuken on 2007-04-04
thanks for your help dude.......

makes sense now......ultimately text files are the way i want to go. i can do the stuff with .csv in MATLAB, but VB is new to me so i'm still learning.

i'm going to follow your steps over the weekend and i'll let you know how it works.......

.......may be even release under the GPL , even though its of no use to anyone other than our research group...hehe

thanks

---

