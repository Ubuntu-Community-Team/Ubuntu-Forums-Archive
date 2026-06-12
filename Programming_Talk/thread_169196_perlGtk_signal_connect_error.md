---
title: "perl/Gtk signal_connect error"
date: 2006-05-02
forum: Programming Talk
---

### Post by G|N| on 2006-05-02
i am trying to write a little perl/Gtk app by hand and now i am stuck on this (probably) stupid mistake ](*,) 

when i click on one of the buttons on the dialog, a sub has to be called with extra arguments (textfields, checkbutton) but i can't get the arguments to work in the sub!

```
    
$dialog->signal_connect('response' , sub {
        my ($dialog, $response, @data) = @_;

        if($response eq 'ok'){
            $uid = $data[0]->get_text;
            $passwd = $data[1]->get_text;
            print $uid; #just for testing
            print $passwd; #just for testing
            if ($data[3]->get_active) {
                &write_configFile;
            }
            else {
                &remove_configFile;
            }
            $dialog->destroy;
        }
        else{
          $dialog->destroy;
        }
    },[$txtLogin, $txtPassword, $checkRemember] );       
```

when i press the ok button, i get this error:
```
*** unhandled exception in callback:
***   Can't call method "get_text" on unblessed reference 
```:-k 
this means that $data[0] is unblessed, but how can i solve it?

thanks

---

