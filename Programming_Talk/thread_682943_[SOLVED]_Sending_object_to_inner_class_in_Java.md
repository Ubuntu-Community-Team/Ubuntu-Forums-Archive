---
title: "[SOLVED] Sending object to inner class in Java"
date: 2008-01-30
forum: Programming Talk
---

### Post by mike_g on 2008-01-30
I'm trying to add focus listeners to an object. The problem is that the object is in an array and the array index cant be found in the inner class because its out of scope. I tried making a temp object but that dosent change the problem. Does someone know how I can get the object the listener is set on from within the inner class? Heres my code:
```
            // Set action listener for cost focus loss, changing content to 0
            // if not a valid double
            JTextField temp = menuItemCosts[i];
            menuItemCosts[i].addFocusListener(new FocusListener()
            {
                public void focusGained(FocusEvent e)
                {

                }
                public void focusLost(FocusEvent e) 
                {
                    double test;
                    try
                    {
                        test = Double.parseDouble(temp.getText());
                    }
                    catch(NumberFormatException ex)
                    {
                        temp.setText("0.00");
                        
                    }
                }
            });
```
Cheers.

---

### Post by CptPicard on 2008-01-30
If I understand this right, you could call your FocusEvent's "getSource()" or "getComponent()" to get get a pointer to the "temp" object?

---

### Post by mike_g on 2008-01-30
At first I couldn't get it to work, but then I realized that I had to cast the return value from getSource(). Its all working now, thanks a lot for the fast reply :)

---

