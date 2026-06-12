---
title: "Ubuntu 16.04 LTS 64 bit: python virtual environment"
date: 2018-02-25
forum: Programming Talk
---

### Post by erotavlas on 2018-02-25
Hi,
I would like to install a python virtual environment on ubuntu 16.04 LTS 64 bit. If I use the following procedure from bash, it works well.
```

pip2 install virtualenv virtualenvwrapper
mkvirtualenv facecourse-py2 -p python2
workon facecourse-py2 
pip install numpy scipy matplotlib scikit-image scikit-learn ipython jupyter pandas sympy nose pyqt5
deactivate

```
Now, I would like to put the same procedure in a bash script executed as root. For what I know is better to avoid to install python as root user (sudo -H -u user).
```

user=$(logname)
if [[ -n "$user" ]]; then # for ubuntu mate
    sudo -H -u $user pip2 install virtualenv virtualenvwrapper
else # for lubuntu for which logname is empty
    sudo -H pip2 install virtualenv virtualenvwrapper
fi

```
The following code does not work inside a bash script both with or without sudo -H or sudo -H -u user.
```

sudo -H mkvirtualenv facecourse-py2 -p python2
sudo -H workon facecourse-py2 
sudo -H pip install numpy scipy matplotlib scikit-image scikit-learn ipython jupyter pandas sympy nose pyqt5
sudo -H deactivate

```
Do you have any suggestion?
Thank you

---

### Post by erotavlas on 2018-02-26
Hi,
I solved by running inside the script:
```

source /usr/local/bin/virtualenvwrapper.sh

```
Now I can run inside the script:
```

mkvirtualenv facecourse-py2 -p python2
workon facecourse-py2
pip -H install numpy scipy matplotlib scikit-image scikit-learn ipython jupyter pandas sympy nose pyqt5
deactivate

```

---

### Post by monkeybrain20122 on 2018-02-26
Why do you want to execute the script with sudo? It seems to be a case of abusing sudo for no good reason.

---

### Post by erotavlas on 2018-02-26
> **monkeybrain20122 said:**
> Why do you want to execute the script with sudo? It seems to be a case of abusing sudo for no good reason.

Hi,
because I need a script that install a lot of software that requires apt-get and the access to several directory under root write permissions.
Do you have a better way to achieve this?

---

