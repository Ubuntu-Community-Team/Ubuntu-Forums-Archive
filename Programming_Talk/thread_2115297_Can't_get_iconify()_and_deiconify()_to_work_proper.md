---
title: "Can't get iconify() and deiconify() to work properly."
date: 2013-02-12
forum: Programming Talk
---

### Post by leonmaxx on 2013-02-12
I'm writing app for Ubuntu Unity with C++ and Gtkmm. In my app i use libappindicator to show icon with simple menu in notification area. Icon and menu works ok, i can minimize window to panel (using iconify() method) with user action on popup menu, but deiconify() method not working, window stays minimized on panel. The only way to restore window is to activate it manually clicking on panel icon.

Here is some code:

```
class CMainWindow: public Gtk::Window {
...
    Glib::RefPtr<Gtk::StyleContext>     m_rStyle;
    Glib::RefPtr<Gtk::UIManager>        m_rUIManager;
    Glib::RefPtr<Gtk::ActionGroup>      m_rActionGroup;
...
public:
...
    void                TrayInit();
    void                TrayWinShow();
    void                TrayWinExit();
... 
};

// this method is called from CMainWindow constructor
void CMainWindow::TrayInit() {
    m_rActionGroup = Gtk::ActionGroup::create();

    m_rActionGroup->add(Gtk::Action::create("Show", "Show"),
        sigc::mem_fun(*this, &CMainWindow::TrayWinShow));
    m_rActionGroup->add(Gtk::Action::create("Hide", "Hide"),
        sigc::mem_fun(*this, &CMainWindow::TrayWinHide));

    m_rUIManager = Gtk::UIManager::create();
    m_rUIManager->insert_action_group(m_rActionGroup);
    add_accel_group(m_rUIManager->get_accel_group());

    Glib::ustring strUI =
            "<ui>"
            "  <popup name='IndicatorPopup'>"
                "    <menuitem action='Show' />"
            "    <menuitem action='Hide' />"
            "  </popup>"
            "</ui>";

    m_rUIManager->add_ui_from_string(strUI);

    Gtk::Widget *pWidget;
    pWidget = m_rUIManager->get_widget("/ui/IndicatorPopup");

    m_pAppIcon = app_indicator_new("sample", "sample_icon",
        APP_INDICATOR_CATEGORY_APPLICATION_STATUS);
    app_indicator_set_status(m_pAppIcon, APP_INDICATOR_STATUS_ACTIVE);
    app_indicator_set_menu(m_pAppIcon, GTK_MENU(pWidget->gobj()));
}

void CMainWindow::TrayWinShow() {
    deiconify();
}

void CMainWindow::TrayWinHide() {
    iconify();
}

```
Also I tried to use hide()/show() methods:

```
void CMainWindow::TrayWinShow() {
    show();
    get_application()->release();
}

void CMainWindow::TrayWinHide() {
    get_application()->hold();
    hide();
}

```
This variant properly hides window but when it calls show() i get a segfault.

Can anyone point me to what i'm doing wrong?

---

