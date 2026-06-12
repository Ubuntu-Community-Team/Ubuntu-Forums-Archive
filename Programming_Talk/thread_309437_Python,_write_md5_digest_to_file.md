---
title: "Python, write md5 digest to file"
date: 2006-11-29
forum: Programming Talk
---

### Post by Jimmy_r on 2006-11-29
I am trying to get SUM(see signature) to write the grub password in encrypted form to menu.lst. Currently it writes the password in plain-text and that is not too clever...

This is the function I currently use:
```
def on_update_password_button_clicked(self, widget):
                if self.password_entry.get_text() == self.confirm_password_entry.get_text():
                        password=self.password_entry.get_text()
                        if self.password_protect_check.get_active():
                                change_config("password", None, "password "+password+"\n")
                        else:
                                change_config("password", None, "#password "+password+"\n")

                        self.password_notify_label_mismatch.hide()
                        self.password_notify_label_updated.show()

                else:
                        self.password_notify_label_updated.hide()
                        self.password_notify_label_mismatch.show()
```
And here is the "change_config" function:
```
def change_config(identifier, old_value, new_value):
        """Changes the configuration file based on the passed values."""
        line_number=get_line_number(identifier)
        lines=get_lines_of_file(Config.menu)
        line=lines[line_number]
        if old_value == None:
                lines[line_number]=new_value
        elif old_value == "vga=":
                place=line.find(old_value)
		if place != -1:
                        line=line[:place]+new_value+line[place+7:]
                else:
                        place=line.find("\n")
                        line=line[:-1]+" "+new_value+"\n"
                lines[line_number]=line
        else:
                if old_value[0] != "#" and line.find(" "+old_value) != -1:
                        old_value=" "+old_value

                if old_value[0] == "#" and line.find("# "+old_value[1:]) != -1:
                        old_value="# "+old_value[1:]

                line=line.replace(old_value, new_value)
                lines[line_number]=line

        output_file=open(Config.menu, 'w')
        for out_line in lines:
                output_file.write(out_line)
        output_file.close()
```

What would be the best way to send an encrypted password to the file instead?
I tried the python md5 module, but the encrypted password corrupts the file if passed through the change_config function(or if it is written directly)

I also thought about using the grub-md5-crypt program and pipe the output through sed or something, but I have no idea how to send the user-submitted password to grub-md5-crypt.

Any help is appreciated.

---

