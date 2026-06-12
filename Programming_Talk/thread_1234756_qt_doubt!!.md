---
title: "qt doubt!!"
date: 2009-08-08
forum: Programming Talk
---

### Post by harivittal.hk on 2009-08-08
hi! m new to qt programin..m nt understandin this piece of code..plz help.
here is the code:
"
namespace Ui
{
    class MainWindowClass;
}

class MainWindow : public QMainWindow
{
    Q_OBJECT

public:
    MainWindow(QWidget *parent = 0);
    ~MainWindow();

private:
    Ui::MainWindowClass *ui;
};
"
my doubt is why a class is defined in namespace,is tat allowed..is the word "namespace" a return type or acting as a datatype.
any help is appreciated..:(

---

### Post by smartbei on 2009-08-08
Firstly, please use the [code ] tags - just stick your code between [code ] and [/code ] (without the spaces of course), so that it will look better and stay formatted. (Edit your post)

About your question - I think you should take a look at http://www.cplusplus.com/doc/tutorial/namespaces/ for example - it explains in relative detail what namespaces are and how to use them.

---

