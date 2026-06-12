---
title: "Displaying content of jTable in different area (java)"
date: 2007-12-12
forum: Programming Talk
---

### Post by jinxen on 2007-12-12
Hi! I have a jTable which is showing the title of a private message retrieved from a mysql database. When clicking on that titles message i want to show the content in a different area, maybe a text area or what is best. But i can't find any method thats in my liking :)

Any help is appreciated!

Cheers, Tommy

Or myabe someone knows how to return the text of the selected row? If i am able to do that i can compare with what i need in the mysql database. Returning the index of the selected row does not help, i can't find any metohod for returning the text of the selected row!

---

### Post by jinxen on 2007-12-12
Ok, i have gotten above problem to work. But to a new problem. The following code is applied to a function that sends a pm. But every time i presses the send button it locks my application. Why?

```

public static void skickaPm() {
    Statement s = null;
            try {
                s = c.createStatement();
                } catch (SQLException se) {
      System.out.println("We got an exception while creating a statement:" +
          "that probably means we're no longer connected.");
      se.printStackTrace();
      System.exit(1);
    }
    
    try {
    /*
    quote
    */
    String avsandare = "tommy";
    String mottagare = gui.SkickaPm.mottagareTextField.getText();
    String amne = gui.SkickaPm.amneTextField.getText();
    String innehall = gui.SkickaPm.innehallTextArea.getText();
    
   //i = s.executeUpdate("INSERT INTO pm(author, receptient, subject, content) " + "VALUES ('"+avsandare+"', '"+mottagare+"', '"+amne+"', '"+innehall+"')");
    //i = s.executeUpdate("INSERT INTO pm(author) VALUES ('"+avsandare+"')");
    String updateString = "INSERT INTO pm(author) VALUES ('nils')";
    s.executeUpdate(updateString);
    s.close();
    
    } catch (SQLException se) {
    System.out.println("We got an exception while executing our query:" +
      "that probably means our SQL is invalid");
    se.printStackTrace();
    System.exit(1);
}


}
}

```

I have also tried using s.execute instead of s.executeUpdate.

---

