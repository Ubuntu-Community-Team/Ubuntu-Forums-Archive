---
title: "Sorry, but how do I run this..."
date: 2009-11-06
forum: Programming Talk
---

### Post by I-Know-Nothing on 2009-11-06
I need to install this, but have no idea how to. Please help me. Thanks.

P.S. The file is "install.sh" and lives /josh/home/desktop. Please tell me exactly what to type. Thanks

P.P.S I'm running Kubuntu 9.04 for the first time. 

> #!/bin/sh 
VERSION="0.9.5"
NAME="mountiso"
FULLNAME="Mount-ISO"
SUDO="sudo"
SU="kdesu"
DE="kde"

SYSTEM="`kde-config --prefix 2>/dev/null`"
LOCAL="`kde-config --localprefix 2>/dev/null`"
DESKTOP="`kde-config --userpath desktop 2>/dev/null`"
# start data extractor prefix
EXTRACT="$HOME/Desktop/$FULLNAME/extracted/usr"
# end data extractor prefix

MENU_HEAD='X-KDE-Submenu=Manage ISO
X-KDE-Submenu[de]=ISO verwalten
X-KDE-Submenu[es]=Gestión ISO
X-KDE-Submenu[it]=Gestione ISO
X-KDE-Submenu[ru]=ISO &#1086;&#1073;&#1088;&#1072;&#1079;
X-KDE-Submenu[sr]=ISO &#1052;&#1077;&#1085;&#1072;&#1119;&#1077;&#1088;
X-KDE-Submenu[sr@Latn]=ISO Menad&#382;er
X-KDE-Submenu[tr]=ISOlar&#305; Yönet'

MENU_MOUNT='[Desktop Action MountISOImage]
Icon=cdimage
Name=Mount Image
Name[de]=Image einbinden
Name[es]=Montar imagen
Name[it]=Monta immagine
Name[ru]=&#1057;&#1084;&#1086;&#1085;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1090;&#1100; &#1086;&#1073;&#1088;&#1072;&#1079;
Name[sr]=&#1052;&#1086;&#1085;&#1090;&#1080;&#1088;&#1072;&#1112; ISO
Name[sr@Latn]=Montiraj ISO
Name[tr]=&#304;maj&#305; Ba&#287;la'

MENU_UNMOUNT='[Desktop Action UnmountISOImage]
Icon=cdimage
Name=Unmount Image
Name[de]=Image aushängen
Name[es]=Desmontar imagen
Name[it]=Smonta immagine
Name[ru]=&#1054;&#1090;&#1084;&#1086;&#1085;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1090;&#1100; &#1086;&#1073;&#1088;&#1072;&#1079;
Name[sr]=&#1044;&#1077;&#1084;&#1086;&#1085;&#1090;&#1080;&#1088;&#1072;&#1112; ISO
Name[sr@Latn]=Demontiraj ISO
Name[tr]=&#304;maj&#305; Ay&#305;r'

MENU_CREATEISO='[Desktop Action CreateISOImage]
Icon=cdimage
Name=Create ISO Image
Name[de]=ISO-Image erstellen
Name[es]=Crear imagen ISO
Name[it]=Crea immagine ISO
Name[ru]=&#1057;&#1086;&#1079;&#1076;&#1072;&#1090;&#1100; ISO-&#1086;&#1073;&#1088;&#1072;&#1079;
Name[sr]=&#1053;&#1072;&#1087;&#1088;&#1072;&#1074;&#1080; ISO &#1086;&#1076;&#1088;&#1072;&#1079;
Name[sr@Latn]=Napravi ISO odraz
Name[tr]=ISO &#304;maj&#305; Olu&#351;tur'

MENU_GRABISO='[Desktop Action GrabISOImage]
Icon=cdimage
Name=Create ISO Image from CD-ROM
Name[de]=ISO-Image von CD-ROM erstellen
Name[es]=Crear imagen ISO desde un CD
Name[it]=Crea immagine ISO dal CDROM
Name[ru]=&#1057;&#1086;&#1079;&#1076;&#1072;&#1090;&#1100; ISO-&#1086;&#1073;&#1088;&#1072;&#1079; &#1082;&#1086;&#1084;&#1087;&#1072;&#1082;&#1090;-&#1076;&#1080;&#1089;&#1082;&#1072;
Name[sr]=&#1053;&#1072;&#1087;&#1088;&#1072;&#1074;&#1080; ISO &#1086;&#1076;&#1088;&#1072;&#1079; &#1089;&#1072; &#1062;&#1044;-&#1072;
Name[sr@Latn]=Napravi ISO odraz sa CD-a
Name[tr]=CD-ROMdan ISO &#304;maj&#305; Olu&#351;tur'

MENU_CALC='[Desktop Action CalcMD5Sum]
Icon=cdimage
Name=Calculate MD5 Sum
Name[de]=MD5-Prüfsumme berechnen
Name[es]=Calcular suma MD5
Name[it]=Calcola somma MD5
Name[ru]=&#1042;&#1099;&#1095;&#1080;&#1089;&#1083;&#1080;&#1090;&#1100; MD5 &#1089;&#1091;&#1084;&#1084;&#1091;
Name[sr]=&#1048;&#1079;&#1088;&#1072;&#1095;&#1091;&#1085;&#1072;&#1112; &#1052;&#1044;5 &#1089;&#1091;&#1084;&#1091;
Name[sr@Latn]=Izra&#269;unaj MD5 sumu
Name[tr]=MD5 Özetini Hesapla'

MENU_CONV2ISO='[Desktop Action ConvertCONV2ISO]
Icon=cdimage
Name=Convert to ISO
Name[de]=In ISO umwandeln
Name[es]=Convertir a ISO
Name[it]=Converti in ISO
Name[ru]=&#1050;&#1086;&#1085;&#1074;&#1077;&#1088;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1090;&#1100; &#1074; &#1086;&#1073;&#1088;&#1072;&#1079; ISO
Name[sr]=&#1050;&#1086;&#1085;&#1074;&#1077;&#1088;&#1090;&#1091;&#1112; &#1091; ISO
Name[sr@Latn]=Konvertuj u ISO
Name[tr]=ISOya Dönü&#351;tür'

MENU_CHECK='[Desktop Action CheckISOType]
Icon=cdimage
Name=Check ISO Type
Name[de]=ISO-Type prüfen
Name[es]=Comprobar tipo de ISO
Name[it]=Controlli il Tipo di ISO
Name[ru]=&#1055;&#1088;&#1086;&#1074;&#1077;&#1088;&#1080;&#1090;&#1100; &#1090;&#1080;&#1087; ISO-&#1086;&#1073;&#1088;&#1072;&#1079;&#1072;
Name[sr]=&#1055;&#1088;&#1086;&#1074;&#1077;&#1088;&#1080; &#1090;&#1080;&#1087; ISO &#1086;&#1076;&#1088;&#1072;&#1079;&#1072;
Name[sr@Latn]=Proveri tip ISO odraza
Name[tr]=ISO Türünü Denetle'

DESKTOP_IMG='[Desktop Entry]
Type=MimeType
Patterns=*.img;*.IMG
MimeType=application/x-img
Icon=cdimage
Comment=IMG image file
Comment[az]=IMG &#601;ks fayl&#305;
Comment[be]=&#1060;&#1072;&#1081;&#1083; &#1074;&#1086;&#1073;&#1088;&#1072;&#1079;&#1091; IMG
Comment[bg]=&#1060;&#1072;&#1081;&#1083; &#1089;&#1085;&#1080;&#1084;&#1082;&#1072; IMG
Comment[bs]=IMG image datoteka
Comment[ca]=Fitxer d imatge IMG
Comment[cs]=Soubor s IMG obrazem
Comment[cy]=Ffeil delwedd IMG
Comment[da]=IMG billedfil
Comment[de]=IMG-Bilddatei
Comment[el]=&#913;&#961;&#967;&#949;&#943;&#959; &#949;&#953;&#954;&#972;&#957;&#945;&#962; IMG
Comment[es]=Archivo de imagen IMG
Comment[et]=IMG tõmmisefail
Comment[eu]=IMG irudia fitxategia
Comment[fa]=&#1662;&#1585;&#1608;&#1606;&#1583;&#1607;*&#1740; IMG
Comment[fi]=IMG binäärikuva
Comment[fr]=Image IMG
Comment[ga]=Comhad íomhá IMG
Comment[gl]=Ficheiro de imaxe IMG
Comment[he]=&#1511;&#1493;&#1489;&#1509; &#1502;&#1512;&#1488;&#1492; &#1513;&#1500; IMG
Comment[hi]=IMG &#2330;&#2367;&#2340;&#2381;&#2352; &#2347;&#2366;&#2311;&#2354;
Comment[hu]=IMG-képmásfájl
Comment[is]=IMG diskmynd
Comment[it]=File immagine IMG
Comment[ja]=IMG &#12452;&#12513;&#12540;&#12472; &#12501;&#12449;&#12452;&#12523;
Comment[lt]=IMG atvaizdo byla
Comment[mn]=IMG &#1093;&#1101;&#1074; &#1092;&#1072;&#1081;&#1083;
Comment[nb]=IMG bildefil
Comment[nds]=IMG-Bilddatei
Comment[nl]=IMG-beeldbestand
Comment[nn]=IMG-biletfil
Comment[pl]=Plik obrazu systemu plików IMG
Comment[pt]=Ficheiro com imagem IMG
Comment[pt_BR]=Imagem IMG
Comment[ro]=Fi&#351;ier imagine IMG
Comment[ru]=&#1060;&#1072;&#1081;&#1083; &#1086;&#1073;&#1088;&#1072;&#1079;&#1072; IMG
Comment[se]=IMG-govvafiila
Comment[sk]=Obraz disku IMG
Comment[sl]=Podoba plo&#353;&#269;e IMG
Comment[sr]=&#1060;&#1072;&#1112;&#1083; IMG &#1086;&#1076;&#1088;&#1072;&#1079;&#1072;
Comment[sr@Latn]=Fajl IMG odraza
Comment[sv]=IMG-avbildsfil
Comment[ta]=IMG &#2953;&#2992;&#3009;&#2965;&#3021; &#2965;&#3019;&#2986;&#3021;&#2986;&#3009;
Comment[tg]=&#1060;&#1072;&#1081;&#1083;&#1080; &#1090;&#1072;&#1089;&#1074;&#1080;&#1088;&#1080; IMG
Comment[tr]=IMG Dosyas&#305;
Comment[uk]=&#1060;&#1072;&#1081;&#1083; &#1086;&#1073;&#1088;&#1072;&#1079;&#1091; IMG
Comment[uz]=IMG-&#1090;&#1072;&#1089;&#1074;&#1080;&#1088; &#1092;&#1072;&#1081;&#1083;&#1080;
Comment[wa]=Fitchî imådje IMG
Comment[xx]=xxIMG image filexx
Comment[zh_CN]=IMG &#26144;&#20687;&#25991;&#20214;
Comment[zh_TW]=IMG &#26144;&#20687;&#27284;&#26696;'

# -------------------------------------------------------------------------
function check_env {
# parameters:
# - $1 = Description
# - $2 = Default location
# - $3 = Fallback
# -------------------------------------------------------------------------

  if ( test -d "$2" ) then
    DIR="$2"
  elif ( test -d "$3" ) then
    DIR="$3"
  else
    echo
    while ( test ! -d "$DIR" )
    do
      echo "Couldn't find $1!"
      echo -n "Type the full path here or press \"Ctrl+C\" to abort: "
      read DIR
    done
  fi
  DIR="$DIR"
  echo -e "* $1: \E[33m$DIR\E[m"
  
....(it goes on)


---

### Post by Ann.A on 2009-11-06
This is probably more a beginner's forum question, but to run a bash script you need to make sure it is executable:

sudo chmod +x /home/josh/desktop/install.sh

And then run it from its location:

sudo /home/josh/desktop/install.sh

---

### Post by lavinog on 2009-11-07
Do you know why you want to run this script?

---

### Post by geirha on 2009-11-07
That's a poorly written script riddled with bashism ([https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)). It might work better if you change the first line to read ```
#!/bin/bash
```

Oh and do NOT run it with sudo unless the documentation specifies that it is designed to be run with sudo.

---

