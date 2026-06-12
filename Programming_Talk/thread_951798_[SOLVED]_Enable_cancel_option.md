---
title: "[SOLVED] Enable cancel_option?"
date: 2008-10-18
forum: Programming Talk
---

### Post by urk_nono on 2008-10-18
Hello! 

I'm having some trouble closing my program, either by CLOSED_OPTION or by CANCEL_OPTION in JOptionPane.

This is my code where I would like to implement the close, and/or cancel:


```
public void showMessage(String message) {

		try {

			int number = Integer.parseInt(JOptionPane.showInputDialog(message));
			
                        if (number == JOptionPane.CLOSED_OPTION)
				System.exit(0);
			
                        test(number);
			
		} catch (NumberFormatException nfe) {

			showMessage("You must plot in a number");
		}

	}
```

Anyone got any ideas :confused:

---

### Post by urk_nono on 2008-10-18
Solved it finally :)

```
public void showMessage(String message) {

      try {

            String input = JOptionPane.showInputDialog(message);
            int answer = 0;

            if (input == null)
	       System.exit(0);
            else
	       answer = Integer.parseInt(input);

            test(answer);

       } catch (NumberFormatException nfe) {
          
                showMessage("You must plot in an integer");
       }
}
```


Thanks to all who wanted to help :)

---

### Post by -grubby on 2008-10-18
Please place your code in [noparse][code][/noparse] tags, it makes it easier to read

---

