---
title: "Problems with Jcalender and java apperance"
date: 2013-09-18
forum: Programming Talk
---

### Post by Drenriza on 2013-09-18
Hey guys.

Hoping someone in here can help me since i dont know any good java forums.
If you know any, please also let me know.

I'am having a issue where my Jcalender looks different from developing and running modes.
See picture.

Where it is missing the dates for a month along with the week numbers.
This only happends when i rescale the jCalender in developing mode.

If i dont rescale it this happends
see picture2

It shows the date but the object is rescaled from the developing mode to running mode by itself O.o Which i dont understand.

Anyone who can help?

Thanks on advance.
kind regards.

---

### Post by ofnuts on 2013-09-18
You don' t even tell if it's AWT, Swing ot SWT... likely your layout manager, but without seeing your code it's hard to tell...

---

### Post by slickymaster on 2013-09-18
> **Drenriza said:**
> Hey guys.

Hoping someone in here can help me since i dont know any good java forums.
If you know any, please also let me know.

[http://www.javaprogrammingforums.com/](http://www.javaprogrammingforums.com/)

> **Drenriza said:**
> ..I'am having a issue where my Jcalender looks different from developing and running modes.
See picture.

Where it is missing the dates for a month along with the week numbers.
This only happends when i rescale the jCalender in developing mode.

If i dont rescale it this happends
see picture2

It shows the date but the object is rescaled from the developing mode to running mode by itself O.o Which i dont understand.

Anyone who can help?

Thanks on advance.
kind regards.

> **ofnuts said:**
> You don' t even tell if it's AWT, Swing ot SWT... likely your layout manager, but without seeing your code it's hard to tell...

ofnuts is right. What GUI framework are you working with? And what layout manager are you using?

---

### Post by Drenriza on 2013-09-18
I'am not very experienced into Java, so thats why i hadnt pasted the code to it. And i have close to 0 experience with layout managers.
So Netbeans is making it for me when i drop objects, just making the logic behind atm. Learning here.

But ofcurse if you have any good resources you want to link. Your more then welcome.
Sites, books, PDF.s and so on.

Are their like sites where you can share your project, and get others advice on stuff. With some feedback to why they would do stuff differently?

Anyhows.
```

private void initComponents() {

        jPanel1 = new javax.swing.JPanel();
        jScrollPane2 = new javax.swing.JScrollPane();
        jTable1 = new javax.swing.JTable();
        jToggleButton1 = new javax.swing.JToggleButton();
        jCalendar2 = new com.toedter.calendar.JCalendar();

        javax.swing.GroupLayout jPanel1Layout = new javax.swing.GroupLayout(jPanel1);
        jPanel1.setLayout(jPanel1Layout);
        jPanel1Layout.setHorizontalGroup(
            jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGap(0, 100, Short.MAX_VALUE)
        );
        jPanel1Layout.setVerticalGroup(
            jPanel1Layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGap(0, 100, Short.MAX_VALUE)
        );

        setDefaultCloseOperation(javax.swing.WindowConstants.EXIT_ON_CLOSE);

        jTable1.setModel(new javax.swing.table.DefaultTableModel(
            new Object [][] {
                {null, null, null, null},
                {null, null, null, null},
                {null, null, null, null},
                {null, null, null, null}
            },
            new String [] {
                "Title 1", "Title 2", "Title 3", "Title 4"
            }
        ));
        jScrollPane2.setViewportView(jTable1);

        jToggleButton1.setFont(new java.awt.Font("Tahoma", 0, 18)); // NOI18N
        jToggleButton1.setText("Save table");

        javax.swing.GroupLayout layout = new javax.swing.GroupLayout(getContentPane());
        getContentPane().setLayout(layout);
        layout.setHorizontalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(javax.swing.GroupLayout.Alignment.TRAILING, layout.createSequentialGroup()
                .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addGroup(layout.createSequentialGroup()
                        .addGap(60, 60, 60)
                        .addComponent(jToggleButton1))
                    .addGroup(layout.createSequentialGroup()
                        .addContainerGap()
                        .addComponent(jCalendar2, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)))
                .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED, 94, Short.MAX_VALUE)
                .addComponent(jScrollPane2, javax.swing.GroupLayout.DEFAULT_SIZE, 421, Short.MAX_VALUE)
                .addContainerGap())
        );
        layout.setVerticalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(layout.createSequentialGroup()
                .addContainerGap()
                .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addComponent(jScrollPane2, javax.swing.GroupLayout.DEFAULT_SIZE, 350, Short.MAX_VALUE)
                    .addGroup(layout.createSequentialGroup()
                        .addComponent(jCalendar2, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)
                        .addPreferredGap(javax.swing.LayoutStyle.ComponentPlacement.RELATED, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE)
                        .addComponent(jToggleButton1, javax.swing.GroupLayout.PREFERRED_SIZE, 57, javax.swing.GroupLayout.PREFERRED_SIZE)))
                .addContainerGap())
        );

        pack();
        setLocationRelativeTo(null);
    }

```

---

