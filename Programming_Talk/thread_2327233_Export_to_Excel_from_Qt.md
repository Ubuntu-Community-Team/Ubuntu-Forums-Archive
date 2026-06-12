---
title: "Export to Excel from Qt"
date: 2016-06-08
forum: Programming Talk
---

### Post by thietnguu on 2016-06-08
[COLOR=#000000]Hi alls! i create project " export to excell" form Qt creator. it work on windows7 but on ubuntu not work. help me please![/COLOR]

[COLOR=#000000]----[/COLOR]
[COLOR=#000000]QSqlDatabase db = QSqlDatabase::addDatabase("QODBC", "excelexport");[/COLOR]
[COLOR=#000000]if(!db.isValid())[/COLOR]
[COLOR=#000000]{[/COLOR]
[COLOR=#000000]qDebug() << "ExportExcelObject::export2Excel failed: QODBC not supported.";[/COLOR]
[COLOR=#000000]return -2;[/COLOR]
[COLOR=#000000]}[/COLOR]
[COLOR=#000000]// set the dsn string[/COLOR]
[COLOR=#000000]QString dsn = QString("DRIVER={Microsoft Excel Driver (*.xls)};DSN='';FIRSTROWHASNAMES=1;READONLY=FALSE; CREATE_DB=\"%1\";DBQ=%2").[/COLOR]
[COLOR=#000000]arg(excelFilePath).arg(excelFilePath);[/COLOR]
[COLOR=#000000]db.setDatabaseName(dsn);[/COLOR]
[COLOR=#000000]if(!db.open())[/COLOR]

[COLOR=#000000]----[/COLOR]

---

