---
title: "java gtk problem"
date: 2005-12-13
forum: Programming Talk
---

### Post by rattusdatorum on 2005-12-13
I get the following error, when I try to run an application:
(I had no problems running it on gentoo or win2000)
** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)
aborting...

here are the imports
```
import java.awt.BorderLayout;

import java.awt.Component;

import java.awt.TextArea;

import java.awt.event.ActionEvent;

import java.awt.event.ActionListener;

import java.util.Vector;



import javax.swing.JButton;

import javax.swing.JComboBox;

import javax.swing.JFrame;

import javax.swing.JPanel;

import javax.swing.JTabbedPane;

import javax.swing.JTextField;

import javax.swing.UIManager;

import javax.swing.UnsupportedLookAndFeelException;
```

anyone has a clue about what is/could be wrong?

---

### Post by hod139 on 2005-12-15
My guess is that you are using the GNU version of java, not Sun's.  As far as I know (I could be very wrong, someone please correct me if I am) gnu's support of swing is not very good.  I would suggest installing either the blackdown version of java or Sun's version.  Instructions for both can be found [here:]("https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249")

---

