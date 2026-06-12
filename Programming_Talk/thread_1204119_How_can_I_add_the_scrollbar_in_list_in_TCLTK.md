---
title: "How can I add the scrollbar in list in TCL/TK ?"
date: 2009-07-04
forum: Programming Talk
---

### Post by tusharv on 2009-07-04
Hi All,

I am working in TCL/TK.

I have made one drop down list using tk_optionMenu. Now how can I attach the scrollbar with the list box. so that if I have 10 contents in list then it will show only 5 and to see other I can scroll the list.

Thanks,
Tusharv

---

### Post by Wim Sturkenboom on 2009-07-04
Below code is taken from one of my applications under development. Remove what you don't need and modify to meet your requirements.

In this case, the size of the listbox is dynamic, meaning it can be one entry, two entries etc. When the underlaying list contains more than ten entries, it will only show 10 entries.

It shows how to limit the height (set the bold part to a fixed value) and how to use a scrollbar with the listbox.

```

        # calculate height of listbox and limit to 10
        set height [llength $tables]
        if {$height > 10} {
                set height 10
        }
...
...
        # listbox
        ################################################################
        frame $w.label
        pack  $w.label -side top -anchor w -fill y -expand false
        label $w.label.label -text "Tables" -width 15 -anchor w
        pack  $w.label.label -side top -anchor w -padx 5

        frame $w.listbox
        pack  $w.listbox -side top -anchor w -fill both -expand true
        listbox $w.listbox.list -width 25 -height **$height** \
                -listvariable tables \
                -yscrollcommand "$w.listbox.yscroll set" \
                -selectmode single \
                -font $myfont
        scrollbar $w.listbox.yscroll -command "$w.listbox.list yview"
        pack  $w.listbox.list $w.listbox.yscroll -side left -anchor w -padx 5 -pady 5 -expand true -fill y
        $w.listbox.list selection set 0
        focus -force $w.listbox.list

```

Hope it helps

---

### Post by tusharv on 2009-07-06
Hi Wim Sturkenboom,

Thanks for you reply, but your ans really don't help.
As I have told you that I have made the drop-dowm list box using tk_optionMenu.

Here is the code for that.
```
set tabel {a b c d e f g h i j k l m n o p q r s t u v w x y z}


set tabel_opt [tk_optionMenu .tabel tabel_var a]

pack .tabel

$tabel_opt delete 0

for {set i 0} {$i <= [llength $tabel]} {incr i} {
  if {$i == 0} {
    set j "select value"
  } else {
    set j [lindex $tabel [expr $i - 1]]
  }
  
  $tabel_opt insert $i radiobutton -label $j -variable var0 -command \
   {set tabel_var $var0;puts $tabel_var}
}
```

In this code How can I make sure that only 10 contents displays and other displays when I use the scrollbar.

Thanks,
Tusharv

---

### Post by Wim Sturkenboom on 2009-07-06
Very sorry for misunderstanding the question; the word listbox triggered my reply. What you have is NOT a listbox.

Although I'm not familiar with *tk_optionMenu*, I doubt it can be done easily as I don't see any options in the man pages to add scrollbars.

---

### Post by stevescripts on 2009-07-06
+1 what Wim Sturkenboom posted, tk_optionMenu does not support a scrollbar...

You would have to either hack the source (perhaps doable, perhaps not, in any case not a small task) or roll your own megawidget... Off-hand I don't know of any widget set that does what you are asking.

Steve

---

