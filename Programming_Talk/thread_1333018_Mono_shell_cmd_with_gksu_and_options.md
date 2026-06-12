---
title: "Mono shell cmd with gksu and options"
date: 2009-11-21
forum: Programming Talk
---

### Post by doas777 on 2009-11-21
howdy all.

I'm writting a gui for chown as a test project for mono, but i'm having difficulty executing the command with gksu, if the chown sub-command contains an option (in this case, -R).

when the process loads, gksu parses the parameters, and assumes that -R is it's option, not chown's, and then errs out since gksu has no -R option. the stderr prints gksu's usage.

how would you guys handle this?

here is an excerpt of the code in question:
```


protected virtual void OnBtnApplyClicked (object sender, System.EventArgs e){
            try {
                string cmd = genCommand();
                //split cmd to get a process and parameters
                string basecmd = cmd.TrimStart(" ".ToCharArray()).Split(" ".ToCharArray())[0]; //get first word
                cmd =  "`" + cmd.Remove(0, cmd.TrimStart(" ".ToCharArray()).IndexOf(" ")) + "`"; //get everything else.
                //msgbox(basecmd + cmd);
                this.textviewOutput.Buffer.Text += basecmd + cmd;
                
                System.Diagnostics.ProcessStartInfo ps = new System.Diagnostics.ProcessStartInfo(basecmd, cmd);
                ps.RedirectStandardOutput = true;
                ps.RedirectStandardError = true;
                System.Diagnostics.Process proc = new System.Diagnostics.Process();
                proc.StartInfo = ps;
                ps.UseShellExecute = false;
                proc.Start();
                proc.WaitForExit();
                
                string sout = proc.StandardOutput.ReadToEnd();
                this.textviewOutput.Buffer.Text += sout;
                string serr = proc.StandardError.ReadToEnd();
                this.textviewOutput.Buffer.Text += serr;

                
            } catch (Exception ex) {
                this.textviewOutput.Buffer.Text += "Error: " + ex.Message;
            }    
        }
        
        private string genCommand(){
            string cmd = "";
            
             if(this.asAdmin)
                cmd += "gksu ";
            
            if(this.tbOwner.Text != "")
                cmd += "chown ";
            else 
                if(this.tbGroup.Text != "")
                    cmd += "chgrp ";
            
            if(this.recurse)
                cmd += "-R ";
            
            if(this.tbOwner.Text != ""){
                cmd += this.tbOwner.Text;
                if(this.tbGroup.Text != "")
                    cmd += ":" + this.tbGroup.Text + " ";
            } else
                if(this.tbGroup.Text != "")
                    cmd += this.tbGroup.Text + " ";
            
            cmd += " \"" + this.path + "\"";
            
            return cmd;
        }

```what do you all think?

thanks,
franklin

---

### Post by directhex on 2009-11-21
Add a -- parameter. gksu will stop parsing things after that.

---

### Post by doas777 on 2009-11-22
no dice I'm afraid. 
i used this command:
gksu --debug chown --recursive user:users  "/home/user/Public/test1"

and got:
gksu: unrecognized option '--recursive'

both when running via the shell, and when gen'ed through my app.

I've played with the quoting of the command a good bit, but haven't really gotten anywhere with it.

any other ideas?

---

### Post by directhex on 2009-11-22
> **doas777 said:**
> no dice I'm afraid. 
i used this command:
gksu --debug chown --recursive user:users  "/home/user/Public/test1"

and got:
gksu: unrecognized option '--recursive'

both when running via the shell, and when gen'ed through my app.

I've played with the quoting of the command a good bit, but haven't really gotten anywhere with it.

any other ideas?

Try gksu --debug -- chown --recursive user:users  "/home/user/Public/test1"
Note the spaces around the --

---

### Post by doas777 on 2009-11-22
> **directhex said:**
> Try gksu --debug -- chown --recursive user:users  "/home/user/Public/test1"
Note the spaces around the --
interesting! never seen that one before.

it runs via the  shell, but still breaks on Process.Start(). unfortunately mono is giving almost no exception information, so no clue why. it may be indicating that gksu is returning error 2, but can't tell for sure.  I'll play with the quoting some more, and see where that leaves me.

---

### Post by doas777 on 2009-11-22
well, i got it going, with your assistance and a little trimming on my parameters string.

Thank you very much!

---

