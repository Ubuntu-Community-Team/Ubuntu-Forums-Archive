---
title: "c++ cross access to classes methods"
date: 2011-09-29
forum: Programming Talk
---

### Post by giuspen on 2011-09-29
Hi,
I'm not very experienced in cpp (used to work in python).
I have the following problem:

1) I have a main class A (a window) and the methods m_A1 and m_A2
2) I have a little class B (a dialog) with a callback m_B1
3) the class B is instantiated and destroyed inside of m_A1
4) from the callback m_B1 I need to call m_A2

I tried to give to B reference to the instance of A (with 'this') but this solution that worked in python here doesn't.

I tried to declare the class B inside of A to have the methods of A accessible inside of B but I can't understand how to write the code of the methods of B, writing for example the class constructor of B would be
A::B::A::B() but gives syntax errors.

Can anybody poinbt me to an example? thanks in advance.

---

### Post by cgroza on 2011-09-29
Could you show us a small snippet of code demonstrating the problem?

---

### Post by giuspen on 2011-09-29
> **cgroza said:**
> Could you show us a small snippet of code demonstrating the problem?

[PHP]
class Centrino
{
public:
    Centrino();
    virtual ~Centrino();
    
    Gtk::Window  *mp_window;
    
protected:
    ...
    bool  on_window_key_press(GdkEventKey *event);
    void  io_process_incoming_command(char *in_str_complete);
    ...
};

class DebugDialog : public Gtk::Dialog
{
public:
    DebugDialog(const char *title, Gtk::Window& parent, bool modal);
    virtual ~DebugDialog() {};
    
protected:
    void  on_button_send_clicked();
    ...
};

void  Centrino::io_process_incoming_command(char *in_str_complete)
{
    ...
}

bool  Centrino::on_window_key_press(GdkEventKey *event_key)
{
    if(event_key->state & GDK_CONTROL_MASK)
    {
        if((event_key->keyval == GDK_KEY_d) || (event_key->keyval == GDK_KEY_D))
        {
            DebugDialog  dialog("Debug Dialog", *mp_window, true);
            int  response = dialog.run();
        }
    }
    ...
}

void  DebugDialog::on_button_send_clicked()
{
    Glib::ustring  entry_content = m_entry.get_text();
    io_process_incoming_command(entry_content.c_str());
}


[/PHP]

Centrino is the class that I called A, DebugDialog is the class that I called B.
From DebugDialog:: on_button_send_clicked() I need to call Centrino:: io_process_incoming_command().
The class DebugDialog lives inside of Centrino:: on_window_key_press().
Thanks.

---

### Post by PaulM1985 on 2011-09-30
Ok.  There are a couple of options that you can do here.  I don't know about the actual problem, so you can probably pick the best solution for you.

1 - On your dialog there are a series of buttons that you can select and after every button click on the dialog you want to send the message back to the main window.

In this case, you need to provide a reference to your main window class (Centrino) to your dialog.  You can do this by adding a member variable to your dialog class "Centrino *m_pOwningClass" and then setting this in your constructor by passing in the parent class
DebugDialog(const char *title, Gtk::Window& parent, bool modal, Centrino *pOwningClass);

When each button is clicked you would use:
m_pOwningClass->io_process_incoming_command([SOMETHING]);

2 - Only one button is to be clicked on the dialog, then the dialog closes.

Here I would have an enum type as a member of the dialog.  When the button is clicked the dialog sets the enum and closes.  The owning class then gets the enum value from the dialog and does something with it.

If you need me to explain this a little clearer, please let me know.

Paul

---

### Post by giuspen on 2011-09-30
> **PaulM1985 said:**
> Ok.  There are a couple of options that you can do here.  I don't know about the actual problem, so you can probably pick the best solution for you.

1 - On your dialog there are a series of buttons that you can select and after every button click on the dialog you want to send the message back to the main window.

In this case, you need to provide a reference to your main window class (Centrino) to your dialog.  You can do this by adding a member variable to your dialog class "Centrino *m_pOwningClass" and then setting this in your constructor by passing in the parent class
DebugDialog(const char *title, Gtk::Window& parent, bool modal, Centrino *pOwningClass);

When each button is clicked you would use:
m_pOwningClass->io_process_incoming_command([SOMETHING]);

2 - Only one button is to be clicked on the dialog, then the dialog closes.

Here I would have an enum type as a member of the dialog.  When the button is clicked the dialog sets the enum and closes.  The owning class then gets the enum value from the dialog and does something with it.

If you need me to explain this a little clearer, please let me know.

Paul

Clear and working thanks.
Best regards,
Giuseppe.

---

