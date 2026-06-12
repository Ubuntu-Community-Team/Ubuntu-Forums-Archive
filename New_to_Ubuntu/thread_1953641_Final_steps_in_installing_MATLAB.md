---
title: "Final steps in installing MATLAB"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by shivamkalra on 2012-04-06
Hello, I'm relatively new to Linux but trying to permanently switch from Windows. I've purchased the MATLAB 2011a for the school work and I was able to install is successfully by following the steps in guide. Now, I'm not able to open it unless I've root privilege.

The MATLAB is installed in /usr/local/MATLAB/ folder and to run it I use following command below:
 
```
cd /usr/local/MATLAB/R2011a/bin
./matlab
```It opens up the MATLAB gui but with lots of errors in it. I've attached the log of MATLAB error. But When I've root privilege it works perfectly fine.

```
sudo ./matlab
```I'm not sure whats going on. Any help or suggestions would be helpful.

---

### Post by TeoBigusGeekus on 2012-04-06
> java.io.FileNotFoundException: /home/shivam/.matlab/R2012a/MATLABDesktop.xml (Permission denied)
Do you have the above mentioned file in your system?
If so, is it owned by you?
If not, you can change its permissions with
```
sudo chown shivam: /home/shivam/.matlab/R2012a/MATLABDesktop.xml
```

---

### Post by idoitprone on 2012-04-06
> **shivamkalra said:**
> 
The MATLAB is installed in /usr/local/MATLAB/ folder and to run it I use following command below:
 
```
cd /usr/local/MATLAB/R2011a/bin
./matlab
```It opens up the MATLAB gui but with lots of errors in it. I've attached the log of MATLAB error. But When I've root privilege it works perfectly fine.

```
sudo ./matlab
```


if I were you, I might start thinking about extending you class path

add this to the end of .bashrc in home dir

```
export PATH=$PATH:/usr/local/MATLAB/R2011a/bin
```

so you can just type
```
matlab
```

anywhere to run

[http://www.linfo.org/path_env_var.html](http://www.linfo.org/path_env_var.html)

[IMG]chrome://dictionarytip/skin/dtipIconHover.png[/IMG]

---

### Post by shivamkalra on 2012-04-06
Thank you. That solved my problem.

---

### Post by TeoBigusGeekus on 2012-04-06
You're welcome.

---

