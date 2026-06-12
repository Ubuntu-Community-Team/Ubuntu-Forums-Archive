---
title: "Link button to program in Glade"
date: 2015-05-13
forum: Programming Talk
---

### Post by maud2 on 2015-05-13
I'm new to Glade and I just love the possibilities this program has for (beginner) GUI developers. I started making a program with some text and buttons and I would like to assign a button to open gnome-control-center. How can I make a button in Glade open it?

---

### Post by maud2 on 2015-05-14
I figured out how to do it! After some research, I figured out the following would work:

  **1. Import system processes**

  ```
from multiprocessing import Process
import subprocess
```  

this need to be added at the top of AppNameWindow.py.

  **2. Connect a button to an application**

  ```
def on_button1_clicked(self, widget, data=None):
       p = Process(target=self.launch_gcc)
       p.start()

def launch_gcc(self):
       subprocess.call(["gnome-control-center"])' 
```

 With this code you tell button1 to open GNOME Control Center when  clicked. "gcc" in this example is a variable you can change yourself  when adding another button.

  **Adding URL to button**

  You can also add an URL to a button with the following code:

  **1. Import webbrowser**

  ```
import webbrowser 
```

 this need to be added at the top of AppNameWindow.py.

  **2. Connect a button to an URL**

  ```
def on_button3_clicked(self, widget, data=None):
return webbrowser.open ('http://example.com')  
```

With this code you tell button3 to open the webbrowser with "example.com" when clicked.

---

### Post by flaymond on 2015-05-21
Thanks for posting the solution too! It help other beginners! :)

---

