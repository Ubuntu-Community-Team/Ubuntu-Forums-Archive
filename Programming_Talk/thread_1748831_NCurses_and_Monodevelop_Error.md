---
title: "NCurses and Monodevelop Error?"
date: 2011-05-04
forum: Programming Talk
---

### Post by etdsbastar on 2011-05-04
Hello friends,

I am using a .NET program via MonoDevelop and I am getting the following errors (see the screenshot)

Secondly, the code is also showing NCurses error. Also try to rectify that.

Please Help.

Below is the code:
```

using System;
using System.Collections.Generic;
using System.Text;
/* using System.Xml; */
using System.Collections;
using System.IO;
namespace GUI
{
    class ConsoleUI
    {
        public NCurses cur = new NCurses();
        public IntPtr stdscr = new IntPtr();

        static void Main(string[] args)
        {
            ConsoleUI m = new ConsoleUI();
            m.stdscr = m.cur.InitScreen();
            int gTWidth = m.cur.GetMaxX();
            int gTHeight = m.cur.GetMaxY();
            int halfX = gTWidth >> 1;
            int halfY = gTHeight >> 1;

            m.cur.WClear(m.stdscr);
            m.cur.Refresh();
            MenuMain mnu = new MenuMain();
            mnu.StartMenu(m.cur, m.stdscr);

            m.cur.SetCBreak(true);

            m.cur.Refresh();
            m.cur.GetCh();
            m.cur.SetEcho(true);

            m.cur.EndWin();

           // XMLLayOut x = new XMLLayOut();
           // ArrayList menus = x.ReadSubMenuXML();
        }

    }

    public class MenuMain
    {
        public IntPtr subMnu;
        public IntPtr mnuMainHeader;
   
        public string[] subMenuItems;
        public int _width;
        public int _height;
        public int xPos;
        public int yPos;
        public MenuMain()
        {

        }
        public void StartMenu(NCurses c, IntPtr scr)
        {
            MenuMain mnu = new MenuMain();
            int menuItem = -1;
            int menuHeader = 0;
            int key;
            mnu._width = 16;
            mnu._height = 3;
         
               string[] menu = new string[] { "Test Email", "Test Web Data", "Change Settings", "Run", "Quit" };
            MenuMain[] arrayHeaders = mnu.MenuMainBldr(0, 0, mnu._height, mnu._width, menu, c, 0, 0, scr);
         
 
     
            c.Keypad(scr, true);
            c.SetEcho(false);
            for (int i = 0; i < arrayHeaders.Length; i++)
            {
                while ((key = c.GetCh()) != 265)
                {
                   

                    switch (key)
                    {
                        case 258: menuItem++; if (menuItem > arrayHeaders.Length - 1) menuItem = 0; break;
                        case 259: menuItem--; if (menuItem < 0) menuItem = arrayHeaders.Length - 1; break;
                        case 261: menuHeader++; if (menuHeader > arrayHeaders.Length - 1) menuHeader = 0; break;
                        case 260: menuHeader--; if (menuHeader < 0) menuHeader = arrayHeaders.Length - 1; break;
                        case 100: c.PrintW(menuHeader.ToString()); break;
                    }

                    arrayHeaders = mnu.MenuMainBldr(0, 0, mnu._height, mnu._width, menu, c, menuHeader, menuItem, scr);
                }
            }
        }
        public IntPtr SubMenuBldr(int x, int y, int height, int width, string[] text, NCurses window, int selectedMenu, int selectedSubMenu, IntPtr scr, IntPtr subMenuWin)
        {
            if (width == 0) { width = _width; }
            if (height == 0) { height = _height; }
            if (x == 0) { x = 1; }
            if (y == 0) { y = 1; }

         
            IntPtr subMenu = new IntPtr();
            window.InitPair(2, NCColors.Green, NCColors.Black);

            window.InitPair(3, NCColors.Black, NCColors.White);
           // subMenu = window.NewWindow(6, 15, y+5, selectedMenu*16);
            window.AttrOn(subMenu, 2);

           
           
            window.Box(subMenu, 0, 0);

           
            for (int i = 0; i < text.Length; i++)
            {
                if (i == selectedSubMenu ) { window.AttrOn(subMenuWin, 3); }
               // window.MVPrintW(i * 2, selectedMenu * 16, text[i]);
                string spacer = "";
                if (text[i] != "") { spacer = "         "; }
                window.MVWPrintW(subMenuWin, i , selectedMenu*16, text[i] + spacer);
                //window.MVWPrintW(subMenuWin, (i+1) * 15, selectedMenu * 16, "");
                if (i == selectedSubMenu  ) { window.AttrOff(subMenuWin, 3); }
            }

           
            window.WRefresh(subMenuWin);
            window.Refresh();
            return subMenu;
        }
        public IntPtr CreateSubMenuWindow(NCurses window, int x)
        {
          IntPtr subMenuWindow = window.NewWindow(20, x, 5, 0);
          return subMenuWindow;
        }
        public MenuMain[] MenuMainBldr(int x, int y, int height, int width, string[] text, NCurses window, int selectedMenu, int selectedSubMenu, IntPtr scr)
        {
            IntPtr headerWindow = window.NewWindow(height, x * 5, 0, 0);
            IntPtr subMenuWindow = CreateSubMenuWindow(window, x);
            MenuMain[] menuHeaders = new MenuMain[text.Length];
 
            if (width == 0) { width = _width; }
            if (height == 0) { height = _height; }
            if (x == 0) { x = 1; }
            if (y == 0) { y = 1; }
            IntPtr[] menuItem = new IntPtr[text.Length];
           
            for (int i = 0; i < menuItem.Length; i++)
            {
                x = i * width;
                MenuMain thisMenu = new MenuMain();
                menuItem[i] = window.NewWindow(height, width, y, x);
                //
                window.StartColor();
                window.InitPair(1, NCColors.White, NCColors.Black);
                window.InitPair(2, NCColors.Green, NCColors.Black);
                window.AttrOn(menuItem[i], 1);
                if (i == selectedMenu)
                {
                    window.AttrOn(menuItem[i], 2);
                     
                }
                window.Box(menuItem[i], 0, 0);

                window.MVWPrintW(menuItem[i], 1, 1, text[i]);
               thisMenu.mnuMainHeader = menuItem[i];
                   thisMenu.xPos = x;
                thisMenu.yPos = y;
                menuHeaders[i] = thisMenu;
                menuHeaders[i].subMenuItems = GetSubMenuStrings(menuHeaders[i], i);
                if (selectedSubMenu > -1)
                {
                    if (i == selectedMenu)
                    {
                         
                        SubMenuBldr(i*x, y, height, width, menuHeaders[selectedMenu].subMenuItems, window, selectedMenu, selectedSubMenu, scr, subMenuWindow);
                    }
                   

                }

                window.WRefresh(menuItem[i]);
                //window.Refresh();
            }
   
           
            return menuHeaders;
        }
        public string[] GetSubMenuStrings(MenuMain menuM, int item )
        {

            string[] subMenu1 = new string[] { "sub1.1", "sub1.2", "sub1.3", "sub1.4", "sub1.5" };
            string[] subMenu2 = new string[] { "sub2.1", "sub2.2", "sub2.3", "sub2.4", "sub2.5" };
            string[] subMenu3 = new string[] { "sub3.1", "sub3.2", "sub3.3", "sub3.4", "sub3.5" };
            string[] subMenu4 = new string[] { "sub4.1", "sub4.2", "sub4.3", "sub4.4", "sub4.5" };
            string[] subMenu5 = new string[] { "sub5.1", "sub5.2", "sub5.3", "sub5.4", "sub5.5" };

            if (item == 0)
            {
                menuM.subMenuItems = subMenu1;
            }
            if (item == 1)
            {
                menuM.subMenuItems = subMenu2;
            }
            if (item == 2)
            {
                menuM.subMenuItems = subMenu3;
            }
            if (item == 3)
            {
                menuM.subMenuItems = subMenu4;
            }
            if (item == 4)
            {
                menuM.subMenuItems = subMenu5;
            }

            return menuM.subMenuItems;
        }
    }

    public class XMLLayOut
    {

        public XMLLayOut() { }

        public ArrayList ReadSubMenuXML()
        {

            ArrayList subMenuList = new ArrayList();
           
            string path = "...&#8221;;//make this a param or use root directory";
            FileStream fs = new FileStream(path, FileMode.Open, FileAccess.Read, FileShare.ReadWrite);
            XmlDocument xmldoc = new XmlDocument();
            xmldoc.Load(fs);
            XmlNodeList xmlnodes = xmldoc.GetElementsByTagName("SubMenus");
            foreach (XmlNode n in xmlnodes)
            {
                XmlNodeList mNodes = xmldoc.GetElementsByTagName("MenuId");
                foreach (XmlNode s in mNodes)
                {
                    XmlNodeList tNodes = xmldoc.GetElementsByTagName("MenuItem");
                   
                       
                        foreach (XmlNode t in tNodes)
                        {
                            try
                            {
                                subMenuList.Add(t.NextSibling.InnerText);
                            }
                            catch { }
                             
                        }
                 }
             }
           
            fs.Close();
            return subMenuList;
        }
    }
}

```

---

### Post by MadCow108 on 2011-05-04
have you added the curses bindings as assembly reference to the project ?
(project->edit references)

---

### Post by etdsbastar on 2011-05-04
> **MadCow108 said:**
> have you added the curses bindings as assembly reference to the project ?
(project->edit references)

I couldn't find anything like that in references. Will you please tell me any PPA or any package where I can find curses bindings. While browsing the net I found MonoCurses, but I don't know where to download it.

---

### Post by MadCow108 on 2011-05-04
it does not seem packaged yet (also not in the gac according to the page), you'll probably have to build it yourself

---

