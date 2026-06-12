---
title: "Automatin server can't create object"
date: 2008-11-17
forum: Programming Talk
---

### Post by rabbitCode on 2008-11-17
hi guys, i have this java script that request data from an sql database. i've set all ActiveX controls to prompt/enable in 
IE->Tools->Security->Custom Level, but i still get the "Automatin server can't create object" error. i dont know what to do now.  please help, the following is the code:

function Aufruf(){
var rst;
var dsn;
var sql;
var newWindow;
dsn = new ActiveXObject("ADODB.Connection");
rst = new ActiveXObject("ADODB.Recordset");
dsn.Open ("Provider=SQLOLEDB.1;Persist Security Info=False;UserID=myID;Initial Catalog=Projekt;Data Source=MyServer;pwd=mypass");
sql = ("select Special_1, Special_2 from A_Result where Special_1 = 'Nimrod'");
rst.Open (sql, dsn);
newWindow = window.open("","","width=600, height=400,top=200, left=200,scrollbars");
while (!rst.EOF){
newWindow.document.write(rst(0) + " " + rst (1));
newWindow.document.write("<br>");
rst.moveNext();
}
rst.Close();
}

---

