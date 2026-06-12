---
title: "Ubuntu 19.04: QSystemTrayIcon does not emit activated signal on mouse click"
date: 2019-10-23
forum: Programming Talk
---

### Post by anshah on 2019-10-23
I have just installed Ubuntu 19.04 and I'm using the Qt distribution it provides in the apt-get repo. I'm seeing that the QSytemTrayIcon signals do not emit upon mouse click. I'm aware of the issues with "activated" signal so I also connected a slot to listen to the "aboutToShow" signal from the QSystemTrayIcon's context menu which also should emit on mouse click. Neither of these signals are going out.

Here's my code for the QSystemTrayIcon:




```
// Create tray and setup tray icon
void MyClass::createTrayIcon()
{
    m_pTrayIconMenu = new QMenu(this);
    m_pTrayImage    = new QPixmap(IMG_SMALL_NOT_CONNECTED);
    m_pTrayIcon     = new QSystemTrayIcon(this);


    m_pTrayIcon->setContextMenu(m_pTrayIconMenu);


    QIcon icon(*m_pTrayImage);
    m_pTrayIcon->setIcon(icon);
    setWindowIcon(icon);
    m_pTrayIcon->show();


    connect(m_pTrayIconMenu, SIGNAL(aboutToShow()),
            this,            SLOT(onActivated()));
    connect(m_pTrayIcon, SIGNAL(activated(QSystemTrayIcon::ActivationReason)),
            this,        SLOT(onActivated(QSystemTrayIcon::ActivationReason)));
}


// Slot to handle context menu aboutToShow signal
void MyClass::onActivated()
{
    if (!this->isVisible())
    {
        this->show();
    }
    else
    {
        this->hide();
    }
}


// Slot to handle tray icon activated signal
void MyClass::onActivated(QSystemTrayIcon::ActivationReason r)
{
    if (r == QSystemTrayIcon::Trigger)
    {
        if (!this->isVisible())
        {
            this->show();
        }
        else
        {
            this->hide();
        }
    }
}



```In Ubuntu 18.04, the signals all emitted and everything was working fine. In Ubuntu 19.04 the signals do not emit.

I'm using the Qt version provided with 19.04 which is Qt 5.12. GNome version is 3.32.1.

---

