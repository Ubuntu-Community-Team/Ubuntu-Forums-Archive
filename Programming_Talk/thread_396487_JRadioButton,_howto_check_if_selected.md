---
title: "JRadioButton, howto check if selected?"
date: 2007-03-29
forum: Programming Talk
---

### Post by jinxen on 2007-03-29
Hi!
I have a problem. When i create a JRadioButton checklist, and add them to a group. If i do some kind of form and would like to know if a butten is checked or not. I dont only want true or false. I also want the category behind the radiobutton also. see code below

I create a button like this
```

String testString = "Test";
JRadioButton testButton = new JRadioButton(testString);
testButton.setMnemonic(KeyEvent.VK_B);
testButton.setActionCommand(horrorString);

```

To simplefy a little, i would like to know if the button is selected and i would like to take the String, testString i mean also. Beacause the testString is going to be inserted into a sql database later on :)

Anyone know how to do this, that would be great! :)

Tommy

---

### Post by samjh on 2007-03-30
To check whether it is selected:
```
boolean test;
test = testButton.isSelected();
```
The test variable will be true is selected, false if unselected.

To check what the string is:
```
String theString;
theString = testButton.getText();
```
The getText() method can be used in any button component, including radio buttons, to retrieve its string.

---

