---
title: "base Calculator question : can i get any code reference for it?"
date: 2008-03-13
forum: Programming Talk
---

### Post by AlexenderReez on 2008-03-13
when i look at this link --> [http://www.cleavebooks.co.uk/scol/calnumba.htm](http://www.cleavebooks.co.uk/scol/calnumba.htm)

i try googling around but failed to find its code...is there anybody know any link that provide code for that (or similar ....)...(hopefully it is written using c,or c++ or java or python (that i'm able to understand)) i try to find it for learning purpose....


:KS:KS

---

### Post by luisromangz on 2008-03-13
It seems to work using JavaScript code embeded in the source HTML of the webpage.

---

### Post by Can+~ on 2008-03-13
In fact, the javascript is embeded on the page, but without any kind of spacing, indentation or common sense.

```
<!-- devised and written by Frank Tapson January 2002-->
<SCRIPT LANGUAGE="JavaScript1.2">
<!--
var Tis,Msg,Eis,Vin,Dec,NU=16;var OtVA=new Array;ChA=new Array;
function LC(){ChA[1]="01";ChA[2]="012";ChA[3]="0123";ChA[4]="01234";ChA[5]="012345";ChA[6]="0123456";ChA[7]="01234567";ChA[8]="012345678";ChA[9]="0123456789";ChA[10]="0123456789Aa";ChA[11]="0123456789ABab";ChA[12]="0123456789ABCabc";ChA[13]="0123456789ABCDabcd";ChA[14]="0123456789ABCDEabcde";ChA[15]="0123456789ABCDEFabcdef";ChA[16]="0123456789ABCDEFGHJKabcdefghjk";}
function GI(){var In,Res,Ct=0;In=document.UniForm.Unit1.value;In=CS(In);if(In.length>0){if(Tin(In,1)=="N"){return "N"}Res=MD(In,2);if(Res=="N"){return "N"}else{if(!(Res=="E")){Ct++;Tis=1}}}In=document.UniForm.Unit2.value;In=CS(In);if(In.length>0){if(Tin(In,2)=="N"){return "N"}Res=MD(In,3);if(Res=="N"){return "N"}else{if(!(Res=="E")){Ct++;Tis=2}}}In=document.UniForm.Unit3.value;In=CS(In);if(In.length>0){if(Tin(In,3)=="N"){return "N"}Res=MD(In,4);if(Res=="N"){return "N"}else{if(!(Res=="E")){Ct++;Tis=3}}}In=document.UniForm.Unit4.value;In=CS(In);if(In.length>0){if(Tin(In,4)=="N"){return "N"}Res=MD(In,5);if(Res=="N"){return "N"}else{if(!(Res=="E")){Ct++;Tis=4}}}In=document.UniForm.Unit5.value;In=CS(In);if(In.length>0){if(Tin(In,5)=="N"){return "N"}Res=MD(In,6);if(Res=="N"){return "N"}else{if(!(Res=="E")){Ct++;Tis=5}}}In=document.UniForm.Unit6.value;In=CS(In);if(In.length>0){if(Tin(In,6)=="N"){return "N"}Res=MD(In,7);if(Res=="N"){return "N"}else{if(!(Res=="E")){Ct++;Tis=6}}}
In=document.UniForm.Unit7.value;In=CS(In);if(In.length>0){if(Tin(In,7)=="N"){return "N"}Res=MD(In,8);if(Res=="N"){return "N"}else{if(!(Res=="E")){Ct++;Tis=7}}}In=document.UniForm.Unit8.value;In=CS(In);if(In.length>0){if(Tin(In,8)=="N"){return "N"}Res=MD(In,9);if(Res=="N"){return "N"}else{if(!(Res=="E")){Ct++;Tis=8}}}In=document.UniForm.Unit9.value;In=CS(In);if(In.length>0){if(Tin(In,9)=="N"){return "N"}Res=MD(In,10);if(Res=="N"){return "N"}else{if(!(Res=="E")){Ct++;Tis=9}}}In=document.UniForm.Unit10.value;In=CS(In);if(In.length>0){if(Tin(In,10)=="N"){return "N"}Res=MD(In,11);if(Res=="N"){return "N"}else{if(!(Res=="E")){Ct++;Tis=10}}}In=document.UniForm.Unit11.value;In=CS(In);if(In.length>0){if(Tin(In,11)=="N"){return "N"}Res=MD(In,12);if(Res=="N"){return "N"}else{if(!(Res=="E")){Ct++;Tis=11}}}In=document.UniForm.Unit12.value;In=CS(In);if(In.length>0){if(Tin(In,12)=="N"){return "N"}Res=MD(In,13);if(Res=="N"){return "N"}else{if(!(Res=="E")){Ct++;Tis=12}}}
In=document.UniForm.Unit13.value;In=CS(In);if(In.length>0){if(Tin(In,13)=="N"){return "N"}Res=MD(In,14);if(Res=="N"){return "N"}else{if(!(Res=="E")){Ct++;Tis=13}}}In=document.UniForm.Unit14.value;In=CS(In);if(In.length>0){if(Tin(In,14)=="N"){return "N"}Res=MD(In,15);if(Res=="N"){return "N"}else{if(!(Res=="E")){Ct++;Tis=14}}}In=document.UniForm.Unit15.value;In=CS(In);if(In.length>0){if(Tin(In,15)=="N"){return "N"}Res=MD(In,16);if(Res=="N"){return "N"}else{if(!(Res=="E")){Ct++;Tis=15}}}In=document.UniForm.Unit16.value;In=CS(In);if(In.length>0){if(Tin(In,16)=="N"){return "N"}Res=MD(In,20);if(Res=="N"){return "N"}else{if(!(Res=="E")){Ct++;Tis=16}}}if(Ct<1){Eis="NO valid entry detected. ";return "N"}if(Ct>1){Eis="Entry can be made in ONLY ONE box. ";return "N"}return "Y"}
function CS(TI){var TI= ""+TI;var Temp="";SplitString=TI.split(" ");for (var i=0;i<SplitString.length;i++){Temp += SplitString[i];}while (Temp.charAt(0)=="0"){Temp=Temp.substring(1)}return Temp}
function Tin(Nx,Ps){var Te=""+Nx,Allow=ChA[Ps],IsAt;for(var i=0;i<Te.length;i++){var CharIs=Te.charAt(i);IsAt=Allow.indexOf(CharIs);if(IsAt==-1){Eis="One input is NOT a valid number. ";return "N"}}return "Y";}
function MD(B,Ba){if((B=="")||(B==" ")){return "E"}var Ch,Mu=1,Tot=0,Len=B.length;for(var i=Len-1;i>-1;i--){Ch=B.charAt(i);switch(Ch){case"A":case"a":Ch=10;break;case"B":case"b":Ch=11;break;case"C":case"c":Ch=12;break;case"D":case"d":Ch=13;break;case"E":case"e":Ch=14;break;case"F":case"f":Ch=15;break;case"G":case"g":Ch=16;break;case"H":case"h":Ch=17;break;case"J":case"j":Ch=18;break;case"K":case"k":Ch=19;default:break;}Tot=eval(Tot)+eval(Ch*Mu);Mu=Mu*Ba;}Dec=Tot;if(Dec>0&&Dec<10000000){return "Y"}if(Dec>10000000){Eis="Input is too BIG (>10 million). ";return "N"}if(Dec<0){Eis="Input is not understood. ";return "N"}}
function MO(){for(var i=1;i<NU+1;i++){var Rem,Add,Use=Dec,Ga="",Ba=i+1;if(i==16){Ba=20}do{Rem=Use%Ba;Use=Math.floor(Use/Ba);switch(Rem){case 10:Add="A";break;case 11:Add="B";break;case 12:Add="C";break;case 13:Add="D";break;case 14:Add="E";break;case 15:Add="F";break;case 16:Add="G";break;case 17:Add="H";break;case 18:Add="J";break;case 19:Add="K";break;default:Add=Rem}Ga=Add+Ga;}while(Use>0);var Ch,Ct=0,Bu="",Len=Ga.length;for(var k=Len-1;k>-1;k--){Ch=Ga.charAt(k);Ct++;Bu=Ch+Bu;if((Ct%4==0)&&(!(Ct==Len))){Bu=" "+Bu}}OtVA[i]=Bu;}return "Y"}
function LO(){document.UniForm.Message.value="  Click on [Clear All] to re-start.";document.UniForm.Unit1.value=OtVA[1];document.UniForm.Unit2.value=OtVA[2];document.UniForm.Unit3.value=OtVA[3];document.UniForm.Unit4.value=OtVA[4];document.UniForm.Unit5.value=OtVA[5];document.UniForm.Unit6.value=OtVA[6];document.UniForm.Unit7.value=OtVA[7];document.UniForm.Unit8.value=OtVA[8];document.UniForm.Unit9.value=OtVA[9];document.UniForm.Unit10.value=OtVA[10];document.UniForm.Unit11.value=OtVA[11];document.UniForm.Unit12.value=OtVA[12];document.UniForm.Unit13.value=OtVA[13];document.UniForm.Unit14.value=OtVA[14];document.UniForm.Unit15.value=OtVA[15];document.UniForm.Unit16.value=OtVA[16];Vin="Y";return}
function SU(){LC();CA();Vin="N";return}
function CA(){for(var i=0;i<NU+1;i++){OtVA[i]=""}LO();Vin="N";document.UniForm.Message.value="Enter a value in any box below, and then click on [Calculate It]";return}
function CI(){if(Vin=="Y"){LO();return}if(GI()=="N"){document.UniForm.Message.value=Eis+" Click on [Clear All]";return}if(MO()=="N"){document.UniForm.Message.value=Eis+" Click on [Clear All]";return}LO();return}
					// End of JavaScript -->
						</SCRIPT>

```

---

### Post by Lux Perpetua on 2008-03-13
**Edit**: I found a javascript formatter here: [http://elfz.laacz.lv/beautify/](http://elfz.laacz.lv/beautify/)
```
var Tis,
Msg,
Eis,
Vin,
Dec,
NU = 16;
var OtVA = new Array;
ChA = new Array;
function LC() {
    ChA[1] = "01";
    ChA[2] = "012";
    ChA[3] = "0123";
    ChA[4] = "01234";
    ChA[5] = "012345";
    ChA[6] = "0123456";
    ChA[7] = "01234567";
    ChA[8] = "012345678";
    ChA[9] = "0123456789";
    ChA[10] = "0123456789Aa";
    ChA[11] = "0123456789ABab";
    ChA[12] = "0123456789ABCabc";
    ChA[13] = "0123456789ABCDabcd";
    ChA[14] = "0123456789ABCDEabcde";
    ChA[15] = "0123456789ABCDEFabcdef";
    ChA[16] = "0123456789ABCDEFGHJKabcdefghjk";
}

function GI() {
    var In,
    Res,
    Ct = 0;
    In = document.UniForm.Unit1.value;
    In = CS(In);
    if (In.length > 0) {
        if (Tin(In, 1) == "N") {
            return "N"
        }
        Res = MD(In, 2);
        if (Res == "N") {
            return "N"
        } else {
            if (! (Res == "E")) {
                Ct++;
                Tis = 1
            }
        }
    }
    In = document.UniForm.Unit2.value;
    In = CS(In);
    if (In.length > 0) {
        if (Tin(In, 2) == "N") {
            return "N"
        }
        Res = MD(In, 3);
        if (Res == "N") {
            return "N"
        } else {
            if (! (Res == "E")) {
                Ct++;
                Tis = 2
            }
        }
    }
    In = document.UniForm.Unit3.value;
    In = CS(In);
    if (In.length > 0) {
        if (Tin(In, 3) == "N") {
            return "N"
        }
        Res = MD(In, 4);
        if (Res == "N") {
            return "N"
        } else {
            if (! (Res == "E")) {
                Ct++;
                Tis = 3
            }
        }
    }
    In = document.UniForm.Unit4.value;
    In = CS(In);
    if (In.length > 0) {
        if (Tin(In, 4) == "N") {
            return "N"
        }
        Res = MD(In, 5);
        if (Res == "N") {
            return "N"
        } else {
            if (! (Res == "E")) {
                Ct++;
                Tis = 4
            }
        }
    }
    In = document.UniForm.Unit5.value;
    In = CS(In);
    if (In.length > 0) {
        if (Tin(In, 5) == "N") {
            return "N"
        }
        Res = MD(In, 6);
        if (Res == "N") {
            return "N"
        } else {
            if (! (Res == "E")) {
                Ct++;
                Tis = 5
            }
        }
    }
    In = document.UniForm.Unit6.value;
    In = CS(In);
    if (In.length > 0) {
        if (Tin(In, 6) == "N") {
            return "N"
        }
        Res = MD(In, 7);
        if (Res == "N") {
            return "N"
        } else {
            if (! (Res == "E")) {
                Ct++;
                Tis = 6
            }
        }
    }
    In = document.UniForm.Unit7.value;
    In = CS(In);
    if (In.length > 0) {
        if (Tin(In, 7) == "N") {
            return "N"
        }
        Res = MD(In, 8);
        if (Res == "N") {
            return "N"
        } else {
            if (! (Res == "E")) {
                Ct++;
                Tis = 7
            }
        }
    }
    In = document.UniForm.Unit8.value;
    In = CS(In);
    if (In.length > 0) {
        if (Tin(In, 8) == "N") {
            return "N"
        }
        Res = MD(In, 9);
        if (Res == "N") {
            return "N"
        } else {
            if (! (Res == "E")) {
                Ct++;
                Tis = 8
            }
        }
    }
    In = document.UniForm.Unit9.value;
    In = CS(In);
    if (In.length > 0) {
        if (Tin(In, 9) == "N") {
            return "N"
        }
        Res = MD(In, 10);
        if (Res == "N") {
            return "N"
        } else {
            if (! (Res == "E")) {
                Ct++;
                Tis = 9
            }
        }
    }
    In = document.UniForm.Unit10.value;
    In = CS(In);
    if (In.length > 0) {
        if (Tin(In, 10) == "N") {
            return "N"
        }
        Res = MD(In, 11);
        if (Res == "N") {
            return "N"
        } else {
            if (! (Res == "E")) {
                Ct++;
                Tis = 10
            }
        }
    }
    In = document.UniForm.Unit11.value;
    In = CS(In);
    if (In.length > 0) {
        if (Tin(In, 11) == "N") {
            return "N"
        }
        Res = MD(In, 12);
        if (Res == "N") {
            return "N"
        } else {
            if (! (Res == "E")) {
                Ct++;
                Tis = 11
            }
        }
    }
    In = document.UniForm.Unit12.value;
    In = CS(In);
    if (In.length > 0) {
        if (Tin(In, 12) == "N") {
            return "N"
        }
        Res = MD(In, 13);
        if (Res == "N") {
            return "N"
        } else {
            if (! (Res == "E")) {
                Ct++;
                Tis = 12
            }
        }
    }
    In = document.UniForm.Unit13.value;
    In = CS(In);
    if (In.length > 0) {
        if (Tin(In, 13) == "N") {
            return "N"
        }
        Res = MD(In, 14);
        if (Res == "N") {
            return "N"
        } else {
            if (! (Res == "E")) {
                Ct++;
                Tis = 13
            }
        }
    }
    In = document.UniForm.Unit14.value;
    In = CS(In);
    if (In.length > 0) {
        if (Tin(In, 14) == "N") {
            return "N"
        }
        Res = MD(In, 15);
        if (Res == "N") {
            return "N"
        } else {
            if (! (Res == "E")) {
                Ct++;
                Tis = 14
            }
        }
    }
    In = document.UniForm.Unit15.value;
    In = CS(In);
    if (In.length > 0) {
        if (Tin(In, 15) == "N") {
            return "N"
        }
        Res = MD(In, 16);
        if (Res == "N") {
            return "N"
        } else {
            if (! (Res == "E")) {
                Ct++;
                Tis = 15
            }
        }
    }
    In = document.UniForm.Unit16.value;
    In = CS(In);
    if (In.length > 0) {
        if (Tin(In, 16) == "N") {
            return "N"
        }
        Res = MD(In, 20);
        if (Res == "N") {
            return "N"
        } else {
            if (! (Res == "E")) {
                Ct++;
                Tis = 16
            }
        }
    }
    if (Ct < 1) {
        Eis = "NO valid entry detected. ";
        return "N"
    }
    if (Ct > 1) {
        Eis = "Entry can be made in ONLY ONE box. ";
        return "N"
    }
    return "Y"
}

function CS(TI) {
    var TI = "" + TI;
    var Temp = "";
    SplitString = TI.split(" ");
    for (var i = 0; i < SplitString.length; i++) {
        Temp += SplitString[i];
    }
    while (Temp.charAt(0) == "0") {
        Temp = Temp.substring(1)
    }
    return Temp
}

function Tin(Nx, Ps) {
    var Te = "" + Nx,
    Allow = ChA[Ps],
    IsAt;
    for (var i = 0; i < Te.length; i++) {
        var CharIs = Te.charAt(i);
        IsAt = Allow.indexOf(CharIs);
        if (IsAt == -1) {
            Eis = "One input is NOT a valid number. ";
            return "N"
        }
    }
    return "Y";
}

function MD(B, Ba) {
    if ((B == "") || (B == " ")) {
        return "E"
    }
    var Ch,
    Mu = 1,
    Tot = 0,
    Len = B.length;
    for (var i = Len - 1; i > -1; i--) {
        Ch = B.charAt(i);
        switch (Ch) {
        case "A":
        case "a":
            Ch = 10;
            break;
        case "B":
        case "b":
            Ch = 11;
            break;
        case "C":
        case "c":
            Ch = 12;
            break;
        case "D":
        case "d":
            Ch = 13;
            break;
        case "E":
        case "e":
            Ch = 14;
            break;
        case "F":
        case "f":
            Ch = 15;
            break;
        case "G":
        case "g":
            Ch = 16;
            break;
        case "H":
        case "h":
            Ch = 17;
            break;
        case "J":
        case "j":
            Ch = 18;
            break;
        case "K":
        case "k":
            Ch = 19;
        default:
            break;
        }
        Tot = eval(Tot) + eval(Ch * Mu);
        Mu = Mu * Ba;
    }
    Dec = Tot;
    if (Dec > 0 && Dec < 10000000) {
        return "Y"
    }
    if (Dec > 10000000) {
        Eis = "Input is too BIG (>10 million). ";
        return "N"
    }
    if (Dec < 0) {
        Eis = "Input is not understood. ";
        return "N"
    }
}

function MO() {
    for (var i = 1; i < NU + 1; i++) {
        var Rem,
        Add,
        Use = Dec,
        Ga = "",
        Ba = i + 1;
        if (i == 16) {
            Ba = 20
        }
        do {
            Rem = Use % Ba;
            Use = Math.floor(Use / Ba);
            switch (Rem) {
            case 10:
                Add = "A";
                break;
            case 11:
                Add = "B";
                break;
            case 12:
                Add = "C";
                break;
            case 13:
                Add = "D";
                break;
            case 14:
                Add = "E";
                break;
            case 15:
                Add = "F";
                break;
            case 16:
                Add = "G";
                break;
            case 17:
                Add = "H";
                break;
            case 18:
                Add = "J";
                break;
            case 19:
                Add = "K";
                break;
            default:
                Add = Rem
            }
            Ga = Add + Ga;
        }
        while (Use > 0);
        var Ch,
        Ct = 0,
        Bu = "",
        Len = Ga.length;
        for (var k = Len - 1; k > -1; k--) {
            Ch = Ga.charAt(k);
            Ct++;
            Bu = Ch + Bu;
            if ((Ct % 4 == 0) && (!(Ct == Len))) {
                Bu = " " + Bu
            }
        }
        OtVA[i] = Bu;
    }
    return "Y"
}

function LO() {
    document.UniForm.Message.value = "  Click on [Clear All] to re-start.";
    document.UniForm.Unit1.value = OtVA[1];
    document.UniForm.Unit2.value = OtVA[2];
    document.UniForm.Unit3.value = OtVA[3];
    document.UniForm.Unit4.value = OtVA[4];
    document.UniForm.Unit5.value = OtVA[5];
    document.UniForm.Unit6.value = OtVA[6];
    document.UniForm.Unit7.value = OtVA[7];
    document.UniForm.Unit8.value = OtVA[8];
    document.UniForm.Unit9.value = OtVA[9];
    document.UniForm.Unit10.value = OtVA[10];
    document.UniForm.Unit11.value = OtVA[11];
    document.UniForm.Unit12.value = OtVA[12];
    document.UniForm.Unit13.value = OtVA[13];
    document.UniForm.Unit14.value = OtVA[14];
    document.UniForm.Unit15.value = OtVA[15];
    document.UniForm.Unit16.value = OtVA[16];
    Vin = "Y";
    return
}

function SU() {
    LC();
    CA();
    Vin = "N";
    return
}

function CA() {
    for (var i = 0; i < NU + 1; i++) {
        OtVA[i] = ""
    }
    LO();
    Vin = "N";
    document.UniForm.Message.value = "Enter a value in any box below, and then click on [Calculate It]";
    return
}

function CI() {
    if (Vin == "Y") {
        LO();
        return
    }
    if (GI() == "N") {
        document.UniForm.Message.value = Eis + " Click on [Clear All]";
        return
    }
    if (MO() == "N") {
        document.UniForm.Message.value = Eis + " Click on [Clear All]";
        return
    }
    LO();
    return
}

// End of JavaScript

```

---

