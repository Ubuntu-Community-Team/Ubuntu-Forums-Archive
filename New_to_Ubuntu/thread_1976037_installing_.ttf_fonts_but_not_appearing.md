---
title: "installing .ttf fonts but not appearing"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-05-08
Hi All

I am trying to install a bunch of truetype fonts into ubuntu from a font folder.
I created a font sub directory in my /usr/share/fonts
```

glenn@acer:~$ cd /usr/share/fonts
glenn@acer:/usr/share/fonts$ ls
cmap  truetype  type1  X11
glenn@acer:/usr/share/fonts$ cd truetype
glenn@acer:/usr/share/fonts/truetype$ mkdir fonts
mkdir: cannot create directory `fonts': Permission denied
glenn@acer:/usr/share/fonts/truetype$ sudo mkdir fonts
glenn@acer:

```I then copied my truetype (.ttf) fonts from my Seagate drive and into my new 'fonts directory':
```

glenn@acer:cd /media/Seagate/Font Library$
glenn@acer:cd /media/Seagate/Font Library$ls
A Beat By Kai.otf
A Beat by Kai.ttf 
Aleia Abnormal.TTF 
Alix2.ttf 
...
glenn@acer:/media/Seagate/Font Library$ 
glenn@acer:/media/Seagate/Font Library$ sudo cp *.ttf /usr/share/fonts/truetype/fonts/
glenn@acer:/media/Seagate/Font Library$ cd /usr/share/fonts/truetype/fonts
glenn@acer:/usr/share/fonts/truetype/fonts$ ls
A Beat by Kai.ttf
Alix2.ttf
...
glenn@acer:/usr/share/fonts/truetype/fonts$

```Then I change the owner of the fonts to root and run fc-cache so Ubuntu knows the fonts are installed:
```

glenn@acer:/usr/share/fonts/truetype/fonts$ sudo chown root *.ttf
glenn@acer:/usr/share/fonts/truetype/fonts$ cd ..
glenn@acer:/usr/share/fonts/truetype$ fc-cache
glenn@acer:/usr/share/fonts/truetype$

```But when I run a program such as LibreOffice Writer, the fonts aren't displayed in the fonts drop-down menu.
What am I not doing?

And just to double check the fonts are where I put them:
```

glenn@acer:/usr/share/fonts/truetype$ cd fonts
glenn@acer:/usr/share/fonts/truetype/fonts$ ls
A Beat by Kai.ttf                       OrchideeMedium.ttf
Alix2.ttf                               Oregon LDO Black Oblique.ttf
Anarchistic®.ttf                        Oregon LDO Black Sinistral.ttf
Architect Bold.ttf                      Oregon LDO Black.ttf
Arctitect Regular.ttf                   Oregon LDO Bold Oblique.ttf
Art Brush Medium.ttf                    Oregon LDO Bold.ttf
Babelfish.ttf                           Oregon LDO Book Oblique.ttf
Big Mister C.ttf                        Oregon LDO Book Sinistral.ttf
Binky.ttf                               Oregon LDO Book.ttf
Bobs Frantic.ttf                        Oregon LDO Condensed Black Oblique.ttf
Bordeaux Light Regular.ttf              Oregon LDO Condensed Black.ttf
Calligraffiti.ttf                       Oregon LDO Condensed Bold Oblique.ttf
Champagne & Limousines Bold Italic.ttf  Oregon LDO Condensed Bold.ttf
Champagne & Limousines Bold.ttf         Oregon LDO Condensed Oblique.ttf
Champagne & Limousines Italic.ttf       Oregon LDO Condensed.ttf
Champagne & Limousines.ttf              Oregon LDO DemiBold Oblique.ttf
Cherry Cream Soda.ttf                   Oregon LDO DemiBold Sinistral.ttf
Cracked Johnnie.ttf                     Oregon LDO DemiBold.ttf
Crushed.ttf                             Oregon LDO Extended Black Oblique.ttf
Dam It!.ttf                             Oregon LDO Extended Black.ttf
Daniel black.ttf                        Oregon LDO Extended Bold Oblique.ttf
Daniel bold.ttf                         Oregon LDO Extended Bold.ttf
Daniel.ttf                              Oregon LDO Extended Oblique.ttf
DasRiese Shadow.ttf                     Oregon LDO Extended.ttf
Desyrel.ttf                             Oregon LDO ExtraBlack Oblique.ttf
Dirty Darren.ttf                        Oregon LDO ExtraBlack Sinistral.ttf
Domestic Manners.ttf                    Oregon LDO ExtraBlack.ttf
Ducky.ttf                               Oregon LDO ExtraBold Oblique.ttf
Eclipse.ttf                             Oregon LDO ExtraBold Sinistral.ttf
Ecolier_Court.ttf                       Oregon LDO ExtraBold.ttf
Ecolier.ttf                             Oregon LDO Light Oblique.ttf
Elliot Six.ttf                          Oregon LDO Light Sinistral.ttf
Eva 16.ttf                              Oregon LDO Light.ttf
Exploding Sheep.ttf                     Oregon LDO Medium Oblique.ttf
F-ck Beans Bold Italic.ttf              Oregon LDO Medium Sinistral.ttf
F-ck Beans Bold.ttf                     Oregon LDO Medium.ttf
F-ck Beans Italic.ttf                   Oregon LDO Oblique.ttf
F-ck Beans.ttf                          Oregon LDO Sinistral Bold.ttf
Geosans Light Oblique.ttf               Oregon LDO Sinistral.ttf
Geosans Light.ttf                       Oregon LDO.ttf
Go Boom!.ttf                            Oregon LDO UltraBlack Oblique.ttf
Good Foot.ttf                           Oregon LDO UltraBlack Sinistral.ttf
Harabara Hand Itallic.ttf               Oregon LDO UltraBlack.ttf
HeadlineNEWS.ttf                        Oregon LDO Vanishing Bold Oblique.ttf
Herbert.ttf                             Oregon LDO Vanishing Bold.ttf
Hiruko Black Alternative.ttf            Oregon LDO Vanishing Oblique.ttf
HopalongBold.ttf                        Oregon LDO Vanishing.ttf
Hopalong.ttf                            Panzer.ttf
IdolWild.ttf                            !PaulMaul Bold.ttf
In His Hands.ttf                        !PaulMaul.ttf
InkBurrow.ttf                           Peanuts.ttf
j'aime le poisson !.ttf                 Phaeton John.ttf
Jeffrey Print JL Bold Italic.ttf        Poilet Taper.ttf
Jeffrey Print JL Bold.ttf               P.O.S 3000.ttf
Jeffrey Print JL Condensed Italic.ttf   Print Bold.ttf
Jeffrey Print JL Condensed.ttf          Print Clearly.ttf
Jeffrey Print JL Italic.ttf             Printer.ttf
Jeffrey Print JL.ttf                    PROFFESIONAL.ttf
Jeffrey Print JL Wide Italic.ttf        Promised Freedom.ttf
Jeffrey Print JL Wide.ttf               Rabiohead.ttf
Jinky.ttf                               Rock Salt.ttf
Journal.ttf                             Rx Five Five.ttf
jr! Hand.ttf                            Rx Five One.ttf
Kabob Light Regular.ttf                 Rx Five Zero.ttf
KathleenieFont.ttf                      Rx One Five.ttf
Kerater Black.ttf                       Rx One One.ttf
Kerater Medium.ttf                      Rx One Zero.ttf
Kerater UltraLight Itallic.ttf          Rx Zero Five.ttf
Kerater UltraLight.ttf                  Rx Zero One.ttf
Kid Kosmic Bold.ttf                     Rx Zero Zero.ttf
Kid Kosmic Italic.ttf                   schulsch.ttf
Kid Kosmic.ttf                          Scribblicious.ttf
Kirby.ttf                               Secret Love.ttf
Krazy Nights.ttf                        Skarpa LT.ttf
Kristi.ttf                              Steiner light.ttf
KR Star Letters.ttf                     Stink Bomb.ttf
Letter O Matic.ttf                      Stroke Dimension.ttf
Limelight.ttf                           Surrendered Heart.ttf
lousy.ttf                               Swansea Bold Itallic.ttf
Luckiest Guy.ttf                        Swansea Bold.ttf
Merleretta.ttf                          Swansea Itallic.ttf
Metro Normal.ttf                        Swansea.ttf
MM Schuldruck.ttf                       Tangerine Bold.ttf
Monotone.ttf                            Tangerine Regular.ttf
Mountains Of Christmas.ttf              Tinet.ttf
Naughties.ttf                           Trash Hand.ttf
Note This.ttf                           Wagnasty.ttf
Old Printing Press.ttf                  Yanone Tagesschrift.ttf
OrchideeLight.ttf
glenn@acer:/usr/share/fonts/truetype/fonts$ 


```

---

### Post by Cheesemill on 2012-05-08
What are the permissions on the fonts?
Can we please have the output of:
```
ls -lh /usr/share/fonts/truetype/fonts
```

Also what is the output of:
```
sudo fc-cache -fv
```

---

### Post by agillator on 2012-05-08
From memory since it has been a while, I think fc-cache needs to be run as root, i.e. sudo fc-cache. Then, if that doesn't solve the problem, try logging out and back in and then running libreoffice - force it to reload fonts.

---

### Post by coffeecat on 2012-05-08
You need to run fc-cache with elevated privileges for root-owned font files. This should do it:

```
sudo fc-cache -fv
```

If you have only one user on your system and don't need them installed system-wide, you can create a ~/.fonts folder (hidden ".fonts" folder in your home) and simply copy the ttf files directly into it. They are available immediately - you don't have to run fc-cache. Or an automated way to do the same to double-click on your ttf files and then the click on the "install font" button.

---

### Post by Senior_Buckethead on 2012-05-08
Part of the process in my earlier post was changing all the .ttf to root:
```

glenn@acer:/usr/share/fonts/truetype/fonts$ ls -lh
total 14M
-rw------- 1 root root  40K May  8 21:28 A Beat by Kai.ttf
-rw------- 1 root root  25K May  8 21:28 Alix2.ttf
-rw------- 1 root root  29K May  8 21:28 Anarchistic®.ttf
-rw------- 1 root root  36K May  8 21:28 Architect Bold.ttf
-rw------- 1 root root  35K May  8 21:28 Arctitect Regular.ttf
-rw------- 1 root root  23K May  8 21:28 Art Brush Medium.ttf
-rw------- 1 root root  37K May  8 21:28 Babelfish.ttf
-rw------- 1 root root  34K May  8 21:28 Big Mister C.ttf
-rw------- 1 root root  56K May  8 21:28 Binky.ttf
-rw------- 1 root root  36K May  8 21:28 Bobs Frantic.ttf
-rw------- 1 root root  36K May  8 21:28 Bordeaux Light Regular.ttf
-rw------- 1 root root  59K May  8 21:28 Calligraffiti.ttf
-rw------- 1 root root  53K May  8 21:28 Champagne & Limousines Bold Italic.ttf
-rw------- 1 root root  51K May  8 21:28 Champagne & Limousines Bold.ttf
-rw------- 1 root root  54K May  8 21:28 Champagne & Limousines Italic.ttf
-rw------- 1 root root  53K May  8 21:28 Champagne & Limousines.ttf
-rw------- 1 root root  49K May  8 21:28 Cherry Cream Soda.ttf
-rw------- 1 root root  36K May  8 21:28 Cracked Johnnie.ttf
-rw------- 1 root root  57K May  8 21:28 Crushed.ttf
-rw------- 1 root root  51K May  8 21:28 Dam It!.ttf
-rw------- 1 root root  87K May  8 21:28 Daniel black.ttf
-rw------- 1 root root  63K May  8 21:28 Daniel bold.ttf
-rw------- 1 root root  51K May  8 21:28 Daniel.ttf
-rw------- 1 root root 210K May  8 21:28 DasRiese Shadow.ttf
-rw------- 1 root root  89K May  8 21:28 Desyrel.ttf
-rw------- 1 root root  64K May  8 21:28 Dirty Darren.ttf
-rw------- 1 root root  70K May  8 21:28 Domestic Manners.ttf
-rw------- 1 root root  31K May  8 21:28 Ducky.ttf
-rw------- 1 root root  34K May  8 21:28 Eclipse.ttf
-rw------- 1 root root  50K May  8 21:28 Ecolier_Court.ttf
-rw------- 1 root root  50K May  8 21:28 Ecolier.ttf
-rw------- 1 root root 104K May  8 21:28 Elliot Six.ttf
-rw------- 1 root root  43K May  8 21:28 Eva 16.ttf
-rw------- 1 root root  54K May  8 21:28 Exploding Sheep.ttf
-rw------- 1 root root  62K May  8 21:28 F-ck Beans Bold Italic.ttf
-rw------- 1 root root  71K May  8 21:28 F-ck Beans Bold.ttf
-rw------- 1 root root  49K May  8 21:28 F-ck Beans Italic.ttf
-rw------- 1 root root  50K May  8 21:28 F-ck Beans.ttf
-rw------- 1 root root  61K May  8 21:28 Geosans Light Oblique.ttf
-rw------- 1 root root  59K May  8 21:28 Geosans Light.ttf
-rw------- 1 root root  26K May  8 21:28 Go Boom!.ttf
-rw------- 1 root root  64K May  8 21:28 Good Foot.ttf
-rw------- 1 root root 110K May  8 21:28 Harabara Hand Itallic.ttf
-rw------- 1 root root  20K May  8 21:28 HeadlineNEWS.ttf
-rw------- 1 root root  31K May  8 21:28 Herbert.ttf
-rw------- 1 root root  85K May  8 21:28 Hiruko Black Alternative.ttf
-rw------- 1 root root  40K May  8 21:28 HopalongBold.ttf
-rw------- 1 root root  39K May  8 21:28 Hopalong.ttf
-rw------- 1 root root  55K May  8 21:28 IdolWild.ttf
-rw------- 1 root root  27K May  8 21:28 In His Hands.ttf
-rw------- 1 root root  48K May  8 21:28 InkBurrow.ttf
-rw------- 1 root root  23K May  8 21:28 j'aime le poisson !.ttf
-rw------- 1 root root  82K May  8 21:28 Jeffrey Print JL Bold Italic.ttf
-rw------- 1 root root  80K May  8 21:28 Jeffrey Print JL Bold.ttf
-rw------- 1 root root  87K May  8 21:28 Jeffrey Print JL Condensed Italic.ttf
-rw------- 1 root root  88K May  8 21:28 Jeffrey Print JL Condensed.ttf
-rw------- 1 root root  92K May  8 21:28 Jeffrey Print JL Italic.ttf
-rw------- 1 root root  87K May  8 21:28 Jeffrey Print JL.ttf
-rw------- 1 root root  97K May  8 21:28 Jeffrey Print JL Wide Italic.ttf
-rw------- 1 root root  97K May  8 21:28 Jeffrey Print JL Wide.ttf
-rw------- 1 root root 177K May  8 21:28 Jinky.ttf
-rw------- 1 root root 128K May  8 21:28 Journal.ttf
-rw------- 1 root root  57K May  8 21:28 jr! Hand.ttf
-rw------- 1 root root  39K May  8 21:28 Kabob Light Regular.ttf
-rw------- 1 root root  48K May  8 21:28 KathleenieFont.ttf
-rw------- 1 root root  73K May  8 21:28 Kerater Black.ttf
-rw------- 1 root root  71K May  8 21:28 Kerater Medium.ttf
-rw------- 1 root root  54K May  8 21:28 Kerater UltraLight Itallic.ttf
-rw------- 1 root root  68K May  8 21:28 Kerater UltraLight.ttf
-rw------- 1 root root  25K May  8 21:28 Kid Kosmic Bold.ttf
-rw------- 1 root root  25K May  8 21:28 Kid Kosmic Italic.ttf
-rw------- 1 root root  25K May  8 21:28 Kid Kosmic.ttf
-rw------- 1 root root  50K May  8 21:28 Kirby.ttf
-rw------- 1 root root  20K May  8 21:28 Krazy Nights.ttf
-rw------- 1 root root  47K May  8 21:28 Kristi.ttf
-rw------- 1 root root  30K May  8 21:28 KR Star Letters.ttf
-rw------- 1 root root  27K May  8 21:28 Letter O Matic.ttf
-rw------- 1 root root  52K May  8 21:28 Limelight.ttf
-rw------- 1 root root  90K May  8 21:28 lousy.ttf
-rw------- 1 root root  72K May  8 21:28 Luckiest Guy.ttf
-rw------- 1 root root  24K May  8 21:28 Merleretta.ttf
-rw------- 1 root root  40K May  8 21:28 Metro Normal.ttf
-rw------- 1 root root  14K May  8 21:28 MM Schuldruck.ttf
-rw------- 1 root root  24K May  8 21:28 Monotone.ttf
-rw------- 1 root root 155K May  8 21:28 Mountains Of Christmas.ttf
-rw------- 1 root root  89K May  8 21:28 Naughties.ttf
-rw------- 1 root root  51K May  8 21:28 Note This.ttf
-rw------- 1 root root 385K May  8 21:28 Old Printing Press.ttf
-rw------- 1 root root  54K May  8 21:28 OrchideeLight.ttf
-rw------- 1 root root  59K May  8 21:28 OrchideeMedium.ttf
-rw------- 1 root root  86K May  8 21:28 Oregon LDO Black Oblique.ttf
-rw------- 1 root root  86K May  8 21:28 Oregon LDO Black Sinistral.ttf
-rw------- 1 root root  98K May  8 21:28 Oregon LDO Black.ttf
-rw------- 1 root root  98K May  8 21:28 Oregon LDO Bold Oblique.ttf
-rw------- 1 root root 102K May  8 21:28 Oregon LDO Bold.ttf
-rw------- 1 root root 119K May  8 21:28 Oregon LDO Book Oblique.ttf
-rw------- 1 root root 120K May  8 21:28 Oregon LDO Book Sinistral.ttf
-rw------- 1 root root 136K May  8 21:28 Oregon LDO Book.ttf
-rw------- 1 root root  63K May  8 21:28 Oregon LDO Condensed Black Oblique.ttf
-rw------- 1 root root  57K May  8 21:28 Oregon LDO Condensed Black.ttf
-rw------- 1 root root  59K May  8 21:28 Oregon LDO Condensed Bold Oblique.ttf
-rw------- 1 root root  53K May  8 21:28 Oregon LDO Condensed Bold.ttf
-rw------- 1 root root 100K May  8 21:28 Oregon LDO Condensed Oblique.ttf
-rw------- 1 root root  99K May  8 21:28 Oregon LDO Condensed.ttf
-rw------- 1 root root 105K May  8 21:28 Oregon LDO DemiBold Oblique.ttf
-rw------- 1 root root 105K May  8 21:28 Oregon LDO DemiBold Sinistral.ttf
-rw------- 1 root root 121K May  8 21:28 Oregon LDO DemiBold.ttf
-rw------- 1 root root  66K May  8 21:28 Oregon LDO Extended Black Oblique.ttf
-rw------- 1 root root  60K May  8 21:28 Oregon LDO Extended Black.ttf
-rw------- 1 root root  61K May  8 21:28 Oregon LDO Extended Bold Oblique.ttf
-rw------- 1 root root  57K May  8 21:28 Oregon LDO Extended Bold.ttf
-rw------- 1 root root 104K May  8 21:28 Oregon LDO Extended Oblique.ttf
-rw------- 1 root root 102K May  8 21:28 Oregon LDO Extended.ttf
-rw------- 1 root root  87K May  8 21:28 Oregon LDO ExtraBlack Oblique.ttf
-rw------- 1 root root  87K May  8 21:28 Oregon LDO ExtraBlack Sinistral.ttf
-rw------- 1 root root  96K May  8 21:28 Oregon LDO ExtraBlack.ttf
-rw------- 1 root root  88K May  8 21:28 Oregon LDO ExtraBold Oblique.ttf
-rw------- 1 root root  88K May  8 21:28 Oregon LDO ExtraBold Sinistral.ttf
-rw------- 1 root root 102K May  8 21:28 Oregon LDO ExtraBold.ttf
-rw------- 1 root root 107K May  8 21:28 Oregon LDO Light Oblique.ttf
-rw------- 1 root root 118K May  8 21:28 Oregon LDO Light Sinistral.ttf
-rw------- 1 root root 128K May  8 21:28 Oregon LDO Light.ttf
-rw------- 1 root root 105K May  8 21:28 Oregon LDO Medium Oblique.ttf
-rw------- 1 root root 104K May  8 21:28 Oregon LDO Medium Sinistral.ttf
-rw------- 1 root root 122K May  8 21:28 Oregon LDO Medium.ttf
-rw------- 1 root root 113K May  8 21:28 Oregon LDO Oblique.ttf
-rw------- 1 root root 101K May  8 21:28 Oregon LDO Sinistral Bold.ttf
-rw------- 1 root root 111K May  8 21:28 Oregon LDO Sinistral.ttf
-rw------- 1 root root 129K May  8 21:28 Oregon LDO.ttf
-rw------- 1 root root  84K May  8 21:28 Oregon LDO UltraBlack Oblique.ttf
-rw------- 1 root root  83K May  8 21:28 Oregon LDO UltraBlack Sinistral.ttf
-rw------- 1 root root  94K May  8 21:28 Oregon LDO UltraBlack.ttf
-rw------- 1 root root 226K May  8 21:28 Oregon LDO Vanishing Bold Oblique.ttf
-rw------- 1 root root 205K May  8 21:28 Oregon LDO Vanishing Bold.ttf
-rw------- 1 root root 249K May  8 21:28 Oregon LDO Vanishing Oblique.ttf
-rw------- 1 root root 302K May  8 21:28 Oregon LDO Vanishing.ttf
-rw------- 1 root root  39K May  8 21:28 Panzer.ttf
-rw------- 1 root root  67K May  8 21:28 !PaulMaul Bold.ttf
-rw------- 1 root root  67K May  8 21:28 !PaulMaul.ttf
-rw------- 1 root root  82K May  8 21:28 Peanuts.ttf
-rw------- 1 root root  56K May  8 21:28 Phaeton John.ttf
-rw------- 1 root root  63K May  8 21:28 Poilet Taper.ttf
-rw------- 1 root root  29K May  8 21:28 P.O.S 3000.ttf
-rw------- 1 root root 106K May  8 21:28 Print Bold.ttf
-rw------- 1 root root 118K May  8 21:28 Print Clearly.ttf
-rw------- 1 root root  12K May  8 21:28 Printer.ttf
-rw------- 1 root root  28K May  8 21:28 PROFFESIONAL.ttf
-rw------- 1 root root  35K May  8 21:28 Promised Freedom.ttf
-rw------- 1 root root  30K May  8 21:28 Rabiohead.ttf
-rw------- 1 root root 108K May  8 21:28 Rock Salt.ttf
-rw------- 1 root root  54K May  8 21:28 Rx Five Five.ttf
-rw------- 1 root root  54K May  8 21:28 Rx Five One.ttf
-rw------- 1 root root  56K May  8 21:28 Rx Five Zero.ttf
-rw------- 1 root root  55K May  8 21:28 Rx One Five.ttf
-rw------- 1 root root  56K May  8 21:28 Rx One One.ttf
-rw------- 1 root root  57K May  8 21:28 Rx One Zero.ttf
-rw------- 1 root root  52K May  8 21:28 Rx Zero Five.ttf
-rw------- 1 root root  52K May  8 21:28 Rx Zero One.ttf
-rw------- 1 root root  54K May  8 21:28 Rx Zero Zero.ttf
-rw------- 1 root root  35K May  8 21:28 schulsch.ttf
-rw------- 1 root root  46K May  8 21:28 Scribblicious.ttf
-rw------- 1 root root  23K May  8 21:28 Secret Love.ttf
-rw------- 1 root root 190K May  8 21:28 Skarpa LT.ttf
-rw------- 1 root root  14K May  8 21:28 Steiner light.ttf
-rw------- 1 root root  19K May  8 21:28 Stink Bomb.ttf
-rw------- 1 root root 416K May  8 21:28 Stroke Dimension.ttf
-rw------- 1 root root  34K May  8 21:28 Surrendered Heart.ttf
-rw------- 1 root root  51K May  8 21:28 Swansea Bold Itallic.ttf
-rw------- 1 root root  52K May  8 21:28 Swansea Bold.ttf
-rw------- 1 root root  53K May  8 21:28 Swansea Itallic.ttf
-rw------- 1 root root  53K May  8 21:28 Swansea.ttf
-rw------- 1 root root  65K May  8 21:28 Tangerine Bold.ttf
-rw------- 1 root root  61K May  8 21:28 Tangerine Regular.ttf
-rw------- 1 root root  55K May  8 21:28 Tinet.ttf
-rw------- 1 root root  48K May  8 21:28 Trash Hand.ttf
-rw------- 1 root root  24K May  8 21:28 Wagnasty.ttf
-rw------- 1 root root 103K May  8 21:28 Yanone Tagesschrift.ttf
glenn@acer:/usr/share/fonts/truetype/fonts$ 

```And the output of sudo fc-cache -fv..

```

glenn@acer:/usr/share/fonts/truetype/fonts$ sudo fc-cache -fv
[sudo] password for glenn: 
/usr/share/fonts: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 44 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/cmap/adobe-japan2: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/gs-cjk-resource: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 0 fonts, 14 dirs
/usr/share/fonts/truetype/droid: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/fonts: caching, new cache contents: 177 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 13 fonts, 0 dirs
/usr/share/fonts/truetype/liberation: caching, new cache contents: 16 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 60 fonts, 0 dirs
/usr/share/fonts/truetype/nanum: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: caching, new cache contents: 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 17 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lyx: caching, new cache contents: 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ubuntu-font-family: caching, new cache contents: 11 fonts, 0 dirs
/usr/share/fonts/truetype/wqy: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/type1/mathml: caching, new cache contents: 1 fonts, 0 dirs
/usr/X11R6/lib/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/glenn/.fonts: caching, new cache contents: 0 fonts, 1 dirs
/home/glenn/.fonts/Library: caching, new cache contents: 0 fonts, 0 dirs
/var/cache/fontconfig: cleaning cache directory
/home/glenn/.fontconfig: cleaning cache directory
fc-cache: succeeded
glenn@acer:/usr/share/fonts/truetype/fonts$ 

```

---

### Post by Cheesemill on 2012-05-08
Your fonts are only readable by root, no other users have permissions to access them. To fix you need to do:
```
sudo chmod 644 /usr/share/fonts/truetype/fonts/*
sudo fc-cache -fv
```

---

### Post by Senior_Buckethead on 2012-05-08
```

glenn@acer:~$ cd /usr/share/fonts/truetype
glenn@acer:/usr/share/fonts/truetype$ sudo fc-cache -fv
[sudo] password for glenn: 
/usr/share/fonts: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 44 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/cmap/adobe-japan2: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/gs-cjk-resource: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 0 fonts, 14 dirs
/usr/share/fonts/truetype/droid: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/fonts: caching, new cache contents: 177 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 13 fonts, 0 dirs
/usr/share/fonts/truetype/liberation: caching, new cache contents: 16 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 60 fonts, 0 dirs
/usr/share/fonts/truetype/nanum: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: caching, new cache contents: 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 17 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lyx: caching, new cache contents: 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ubuntu-font-family: caching, new cache contents: 11 fonts, 0 dirs
/usr/share/fonts/truetype/wqy: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/type1/mathml: caching, new cache contents: 1 fonts, 0 dirs
/usr/X11R6/lib/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/glenn/.fonts: caching, new cache contents: 0 fonts, 1 dirs
/home/glenn/.fonts/Library: caching, new cache contents: 0 fonts, 0 dirs
/var/cache/fontconfig: cleaning cache directory
/home/glenn/.fontconfig: cleaning cache directory
fc-cache: succeeded
glenn@acer:/usr/share/fonts/truetype$

```
fc-cache is seeing the fonts in the /usr/share/fonts/truetype/font/ directory:
```

/usr/share/fonts/truetype/fonts: caching, new cache contents: 177 fonts, 0 dirs

```
So why are you not working.

I know I could copy the fonts into my ~/.fonts folder, but there is something decidedly off-color with that. I mean fc-cache should install the fonts. It sees them.
This is Linux - its SUPPOSED to work.

Famous last words.

---

### Post by Senior_Buckethead on 2012-05-08
```

glenn@acer:/usr/share/fonts/truetype$ sudo chmod 644 /usr/share/fonts/truetype/fonts/*
glenn@acer:/usr/share/fonts/truetype$ sudo fc-cache -fv
/usr/share/fonts: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 44 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/cmap/adobe-japan2: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/gs-cjk-resource: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 0 fonts, 14 dirs
/usr/share/fonts/truetype/droid: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/fonts: caching, new cache contents: 177 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 13 fonts, 0 dirs
/usr/share/fonts/truetype/liberation: caching, new cache contents: 16 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 60 fonts, 0 dirs
/usr/share/fonts/truetype/nanum: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: caching, new cache contents: 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 17 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lyx: caching, new cache contents: 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ubuntu-font-family: caching, new cache contents: 11 fonts, 0 dirs
/usr/share/fonts/truetype/wqy: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/type1/mathml: caching, new cache contents: 1 fonts, 0 dirs
/usr/X11R6/lib/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/glenn/.fonts: caching, new cache contents: 0 fonts, 1 dirs
/home/glenn/.fonts/Library: caching, new cache contents: 0 fonts, 0 dirs
/var/cache/fontconfig: cleaning cache directory
/home/glenn/.fontconfig: cleaning cache directory
fc-cache: succeeded
glenn@acer:/usr/share/fonts/truetype$ 

```

[SIZE=4][COLOR=Red]Success!!![/COLOR][/SIZE]

Whats chmod 644?

---

### Post by Senior_Buckethead on 2012-05-08
Excuse my 'having to have a procedure for everything', but to install a new font into the /usr/share/fonts/truetype/fonts/ directory and make it system wide:

To install .ttf fonts, copy the font to /usr/share/fonts/truetype/fonts/
then change the permission of the font: sudo chmod 644 [filename]
Then, run the command: sudo fc-cache -fv

Is that correct?

---

### Post by coffeecat on 2012-05-08
> **Senior_Buckethead said:**
> Excuse my 'having to have a procedure for everything', but to install a new font into the /usr/share/fonts/truetype/fonts/ directory and make it system wide:

To install .ttf fonts, copy the font to /usr/share/fonts/truetype/fonts/
then change the permission of the font: sudo chmod 644 [filename]
Then, run the command: sudo fc-cache -fv

Is that correct?

I don't know how your fonts came to have 600 permissions, but normally you do not have to chmod. I just did this as a double-check:

1 - create folder in /usr/share/fonts/ with "sudo mkdir".
2 - copied ttf files into the new folder with "sudo cp". Note that they were automatically assigned root ownership.
3 - Ran "sudo fc-cache -fv"
4 - Opened Libre-Office - fonts were available for use.

Your original chown to root was unnecessary, but that should not have assigned restrictive permissions.

---

### Post by Senior_Buckethead on 2012-05-08
[http://www.wikihow.com/Install-TrueType-Fonts-on-Ubuntu](http://www.wikihow.com/Install-TrueType-Fonts-on-Ubuntu)

is where I found my initial procedure on how to install .ttf fonts.

---

