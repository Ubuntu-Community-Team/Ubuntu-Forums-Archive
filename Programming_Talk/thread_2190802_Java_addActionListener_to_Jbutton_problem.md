---
title: "Java: addActionListener to Jbutton problem"
date: 2013-11-29
forum: Programming Talk
---

### Post by erotavlas on 2013-11-29
Hi,

I'm new of Java and I have a trouble with Jbutton. I learned that I can add an addActionListener to Jbutton as follow:
```

Jbutton Button1 = new Jbutton("1");
Button1.addActionListener(new ActionListener() {
                public void actionPerformed(ActionEvent arg0) {
}
}

```
The Jbutton is contained inside a Jdialog together with other Jlabels and Jlist, the code is standard. In the code, I call a function that contains the Jbutton listener. The first time that the function is called, when the Jbutton is activated is executed the code inside the body and all work well. Then when I press the button for the second time, the code inside the body is executed two times. Then three time and so on. It seems that Jbutton has a sort of counter that is increased each time that the button is pressed. I cannot figure out where could be the problem and I have not found the answer on the web.

Thank you

---

### Post by Erik1984 on 2013-11-29
Where are these lines placed in your code (I guess the button is part of some JPanel)? I can imagine that if the addActionListener() part gets called multiple times it will add an action listener (the same) to the button each time. The actionListeners you previously added are still there so they all get called when you click the button.

---

### Post by erotavlas on 2013-11-30
Ok, you are right. I have solved the problem by moving the listener in  the constructor of the class. Now I have similar problem with a JDialog.  I have two classes and each of them has a different instance of the  same JDialog. The JDialog uses a gridBagContainer and an element of the  container is a Jlist<String>: this is passed to each class in its  constructor and it is owned by a third class.
If I show one of the  class that owns the JDialog per time all works well, but if I show both  the classes together I can see the JDialog filled with the  Jlist<String> only in one of them. So it seems that when I add the  Jlist to the JDialog it acquires the own of the Jlist and the others  classes cannot use it. The following code is located in the constructor  of each class.
```

Dialog = new JDialog();
Dialog.setLayout(new GridBagLayout());
Dialog.setBounds(150, 150, 400, 400);        
GridBagConstraints gbcDialog = new GridBagConstraints();
gbcDialog.gridx = 0;
gbcDialog.gridy = 0;
Dialog.add(myLabel,gbcDialog);
gbcDialog.gridx = 0;
gbcDialog.gridy = 1;
Dialog.add(GetList(),gbcDialog); // here I take the list

```

---

