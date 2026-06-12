---
title: "[Qt4] QTextEdit strange symbols when reading input from QProcess"
date: 2010-12-06
forum: Programming Talk
---

### Post by Kimm on 2010-12-06
I'm writing a Qt4 GUI for R (the statistics program), in which the R-output should be printed in a QTextEdit. Generally its working fine, but sometimes the output seems to get corrupted somehow, since strange characters appear in the QTextEdit. For example:

For example, if I give R the command:
```
competition<-read.table("/competition2.csv",sep=";",header=T)
```

It will appear as (in the QTextEdit):
```
competition<-read.table("competition2.csv",sep=";",he<competition2.csv", sep=";", hea                         der=T)
```

i.e. completely scrambled! It also happens when looking at help pages from time to time, for example:

> 
[B]_G_e_n_e_r_i_c _X-_Y _P_l_o_t_t_i_n_g

_D_e_s_c_r_i_p_t_i_o_n:[/B]

     Generic function for plotting of R objects.  For more details
     about the graphical parameter arguments, see **â&#8364;&#732;parâ&#8364;&#8482;**.


I cant help but think that this has something to do with encoding.. but I cant say for sure. Any ideas what it could be?

Edit:
this is the only code that writes to the QTextEdit:
```

void MainWindow::Output()
{
    QString x = RProcess->readAllStandardOutput().trimmed();

    ui->txtR->insertPlainText(x);;
    ui->txtR->insertPlainText(RProcess->readAllStandardError());
    ui->txtR->ensureCursorVisible();
}

```

---

