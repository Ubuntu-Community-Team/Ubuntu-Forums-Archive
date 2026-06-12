---
title: "Help with Java"
date: 2009-10-02
forum: Programming Talk
---

### Post by humphreybc on 2009-10-02
I have to make a front end GUI for a calculator application for one of my Java paper assignments this weekend, and i'm stuck.

We're given a Calculator class, which has methods that can act on the Calculator object. The two java files are attached.

I'm trying to get the "CalculatorPanel" class' "ActionPerformed" method to send the information of what button was pressed through to the calculator method. Here's the ActionPerformed method in CalculatorPanel:

```

    /* what to do when a button has been pressed */
    public void actionPerformed(ActionEvent aE) {
      JButton whichButton = (JButton) aE.getSource();
      
      if ("+".equals(whichButton.getText())) {
        calc.inOperator("+");
      } else if
        
        ... // stuff goes in here
        
    } else {
        
        int i = 0;
        Scanner scan = new Scanner(whichButton.getText());
        i = scan.nextInt();
        calc.inDigit(i);
        display.setText(calc.getCurrentInput());
      }
      
      display.setText("You pressed " +  whichButton.getText());
    }

```

Where it says "stuff goes in here" what do do next to make it pick up the other operator buttons?

The calculator has + - * = operators, and digits 0 - 9, and a Clear button.

Thanks a lot!
Benjamin

---

### Post by SouthOfHell on 2009-10-02
Your not doing COMP160 @ Otago by any chance are you ;-)

---

### Post by SouthOfHell on 2009-10-02
```

    /* what to do when a button has been pressed */
    public void actionPerformed(ActionEvent aE) {
      JButton whichButton = (JButton) aE.getSource();
      
      if ("+".equals(whichButton.getText())) {
        calc.inOperator("+");
      } else if ("-".equals(whichButton.getText())){
        calc.inOperation("-");
      } else if
        
        ... // continue on...
        
    } else {
        
        int i = 0;
        Scanner scan = new Scanner(whichButton.getText());
        i = scan.nextInt();
        calc.inDigit(i);
        display.setText(calc.getCurrentInput());
      }
      
      display.setText("You pressed " +  whichButton.getText());
    }

```

---

### Post by humphreybc on 2009-10-02
Haha cheers. Yes I may be.... O.o

Okay so I've added the operator if statements... but it still doesn't want to work with the equals.

What am I doing wrong? Updated files attached.

Thanks!

---

### Post by SouthOfHell on 2009-10-03
Sorry mate, your going to have to figure that out for yourself, its not hard though, use the API as a reference to see what the static methods/methods from the hierarchy return.

---

