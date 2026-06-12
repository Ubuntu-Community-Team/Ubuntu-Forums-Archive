---
title: "gtkdialog + glade + bash/dash/sh"
date: 2009-04-30
forum: Programming Talk
---

### Post by librano on 2009-04-30
Hi all!

I am trying to build some simple applications in Linux. I am not a seasoned coder. I have some experience in bash scripting and very minimal knowledge of python. This is why I decided on using gtkdialog with an interface built using Glade and the code written in bash.

Let me mention that I am using Linux Mint Felicia which is based on Ubuntu Intrepid.

However, I am facing some problems with running gtkdialog. I keep getting this error:

```
sh: source: not found
sh: login_server: not found

```

It even appears when I use the example scripts that are provided in the gtkdialog docs. The GUI is displayed but any action that is initiated (clicking a button) gives this error in the terminal.

From my searches, I think the problem lies with the function scripts which contain bashisms... but I am not sure.

Here are the example files I am running.

glade-01.00-entries_functions.sh
```
#! /bin/bash 

gtkdialog --glade-xml=glade-01.00-entries_functions.glade \
          --include=glade-01.00-entries_functions.functions \
          --program=login_window

```

glade-01.00-entries_functions.glade
```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!-- Generated with glade3
	Version: 3.0.1
	Date: Thu Oct 26 22:04:10 2006
	User: pipas
	Host: desktop.otthon
-->
<glade-interface>
  <widget class="GtkWindow" id="login_window">
    <property name="border_width">5</property>
    <property name="title">GtkDialog Example</property>
    <child>
      <widget class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <widget class="GtkFrame" id="frame1">
            <property name="visible">True</property>
            <property name="label_xalign">0,000000</property>
            <child>
              <widget class="GtkAlignment" id="alignment1">
                <property name="visible">True</property>
                <property name="border_width">5</property>
                <property name="left_padding">12</property>
                <child>
                  <widget class="GtkTable" id="table1">
                    <property name="visible">True</property>
                    <property name="n_rows">3</property>
                    <property name="n_columns">2</property>
                    <property name="column_spacing">5</property>
                    <property name="row_spacing">5</property>
                    <child>
                      <widget class="GtkEntry" id="database_entry">
                        <property name="visible">True</property>
                        <property name="activates_default">True</property>
                      </widget>
                      <packing>
                        <property name="left_attach">1</property>
                        <property name="right_attach">2</property>
                        <property name="top_attach">2</property>
                        <property name="bottom_attach">3</property>
                      </packing>
                    </child>
                    <child>
                      <widget class="GtkEntry" id="name_entry">
                        <property name="visible">True</property>
                        <property name="activates_default">True</property>
                        <signal name="realize" handler="whoami"/>
                      </widget>
                      <packing>
                        <property name="left_attach">1</property>
                        <property name="right_attach">2</property>
                        <property name="top_attach">1</property>
                        <property name="bottom_attach">2</property>
                      </packing>
                    </child>
                    <child>
                      <widget class="GtkEntry" id="server_entry">
                        <property name="visible">True</property>
                        <property name="activates_default">True</property>
                        <property name="text">localhost</property>
                      </widget>
                      <packing>
                        <property name="left_attach">1</property>
                        <property name="right_attach">2</property>
                      </packing>
                    </child>
                    <child>
                      <widget class="GtkLabel" id="label4">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">Database:</property>
                      </widget>
                      <packing>
                        <property name="top_attach">2</property>
                        <property name="bottom_attach">3</property>
                      </packing>
                    </child>
                    <child>
                      <widget class="GtkLabel" id="label3">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">Name:</property>
                      </widget>
                      <packing>
                        <property name="top_attach">1</property>
                        <property name="bottom_attach">2</property>
                      </packing>
                    </child>
                    <child>
                      <widget class="GtkLabel" id="label2">
                        <property name="visible">True</property>
                        <property name="label" translatable="yes">Server:</property>
                      </widget>
                    </child>
                  </widget>
                </child>
              </widget>
            </child>
            <child>
              <widget class="GtkLabel" id="label1">
                <property name="visible">True</property>
                <property name="label" translatable="yes">&lt;b&gt;PostgreSQL Login&lt;/b&gt;</property>
                <property name="use_markup">True</property>
              </widget>
              <packing>
                <property name="type">label_item</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="fill">False</property>
          </packing>
        </child>
        <child>
          <widget class="GtkHButtonBox" id="hbuttonbox1">
            <property name="visible">True</property>
            <property name="border_width">5</property>
            <property name="spacing">5</property>
            <property name="layout_style">GTK_BUTTONBOX_END</property>
            <child>
              <widget class="GtkButton" id="cancel_button">
                <property name="visible">True</property>
                <property name="label">gtk-cancel</property>
                <property name="use_stock">True</property>
                <signal name="clicked" handler="echo &quot;hello&quot;" object="objektum neve"/>
                <signal name="clicked" handler="exit:Cancel"/>
              </widget>
            </child>
            <child>
              <widget class="GtkButton" id="ok_button">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="can_default">True</property>
                <property name="has_default">True</property>
                <property name="label">gtk-ok</property>
                <property name="use_stock">True</property>
                <signal name="clicked" handler="login_server &quot;$server_entry&quot; &quot;$name_entry&quot; &quot;$database_entry&quot;"/>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="fill">False</property>
            <property name="position">1</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>
```

glade-01.00-entries_functions.functions
```
#! /bin/bash
# 
# We don't really need this first line but my text editor recognizes it and i
# like the syntax highlight.
#
function login_server() 
{
	xterm -hold -e "psql -h $1 -U $2 -d $3" &
}
```

What is wrong here? I am totally stumped...

---

### Post by geirha on 2009-04-30
Looks like you are running bash-scripts with sh, which won't work by default if the script uses something bash specific.

Either make the scripts executable, and run them directly (this will make the script run by the shell given in the [shebang](http://en.wikipedia.org/wiki/Shebang_(Unix)), "#! /bin/bash"), or run them specifically with bash.

```

./script    # runs the script with the shell given in the shebang.
bash script # runs the script with bash, ignoring the shebang.
sh script   # runs the script with sh, ignoring the shebang. 

```
In ubuntu, sh is by default pointing to /bin/dash, which is a lighter shell that has less features than bash. the source command is a bash-builtin, and is not available in dash, hence the first error message.

---

### Post by librano on 2009-04-30
i made glade-01.00-entries_functions.sh executable and still get the same error...

running 'bash glade-01.00-entries_functions.sh' also gives the same error...

these are the unmodified example scripts in gtkdialog...

---

### Post by geirha on 2009-04-30
Ok, I installed gtkdialog and tested myself, and I did get the same result. I then checked the source code (apt-get source gtkdialog), and this function from src/widgets.c seems to be the culprit:
```
extern gchar *option_include_file;

FILE *
widget_opencommand(
        const char *command)
{
    char *the_line;
    FILE *infile;

    PIP_DEBUG("Opening command: '%s'", command);

    if (option_include_file != NULL) {
        the_line = g_strdup_printf("source %s; %s",
                option_include_file, command);
        infile = popen(the_line, "r");
        g_free(the_line);
    } else {
        infile = popen(command, "r");
    }

    if (infile == NULL)
        g_warning("%s(): %m", __func__);

    return infile;
}

```
In the case of running glade-01.00-entries_functions.sh, it creates a string that looks like «source glade-01.00-entries_functions.functions; login_server "val1" "val2" "val3"», and then passes that string to popen. But [popen](http://manpages.ubuntu.com/manpages/hardy/en/man3/popen.3.html) runs the command in /bin/sh, and not /bin/bash.

It's thus obviously a bug in gtkdialog. The developer(s) probably have /bin/sh pointing to /bin/bash, so they wouldn't get that problem themselves... I recommend you file a bug report on it to get it fixed.

---

### Post by librano on 2009-04-30
thanks. i'll file a bug report.

---

