---
title: "Can't create proper folder link"
date: 2008-04-30
forum: Programming Talk
---

### Post by DemiAlbedo on 2008-04-30
I'm trying to make some changes to kdestop menu (A software program which makes kubuntu's kmenu look like ubuntu's gnome menu) but i'm having some issues. To better understanding what i'm about to ask check this link out. 

http://www.kde-look.org/content/preview.php?preview=3&id=22605&file1=22605-1.png&file2=22605-2.png&file3=22605-3.png&name=KDesktop+Menu

As you can see in the screenshot there is no "pictures" under the desktop tab. I have created a pictures folder with a nice icon, however when you select "pictures" under the desktop tab it does not bring you to the pictures folder in the home directory. I need some assistance creating this link.

Here is the source code for the "home folder" under the desktop tab. 

void MenuDesktop::slotOpenHomeFolder()
{
	KService::Ptr service = KService::serviceByDesktopName(
	                                             QString::fromLatin1("Home") );
	if (! service)
	{
		new KRun( getenv("HOME") );
	}
	else
	{
		KApplication::startServiceByDesktopName( service->name(), QStringList(),
		                                         0, 0, 0, "", true );
	}
}

I'm not a programmer but i figured this code would be the perfect place to start. changing the "home" stuff in the code with "pictures" will not work so don't bother with that. If anyone has any suggestions of how to reedit this code or can show me how to do what I want I would appreciate it.

P.S. Please don't respond to this forum if you are just going to flame about how Ubuntu is better then Kubuntu, why would you want to mimic the gnome menu blah blah blah.

Thanks

---

### Post by LaRoza on 2008-04-30
> **DemiAlbedo said:**
> 
P.S. Please don't respond to this forum if you are just going to flame about how Ubuntu is better then Kubuntu, why would you want to mimic the gnome menu blah blah blah.

Thanks

That is not a problem in this forum.

You don't know any programming?

---

### Post by DemiAlbedo on 2008-04-30
I know a little programming, but i'm no expert. I figured out how to add "pictures" to the desktop tab with an icon and everything and I redesigned a bootsplash for my laptop. I understand c++ but this one particular problem I can't solve.

---

### Post by LaRoza on 2008-04-30
> **DemiAlbedo said:**
> I know a little programming, but i'm no expert. I figured out how to add "pictures" to the desktop tab with an icon and everything and I redesigned a bootsplash for my laptop. I understand c++ but this one particular problem I can't solve.
Isn't there a way to add a link to the menu like there is in GNOME?

---

