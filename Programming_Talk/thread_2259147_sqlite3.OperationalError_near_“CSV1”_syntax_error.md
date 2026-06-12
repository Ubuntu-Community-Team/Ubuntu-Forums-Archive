---
title: "sqlite3.OperationalError: near “CSV1”: syntax error"
date: 2015-01-02
forum: Programming Talk
---

### Post by amy8 on 2015-01-02
[COLOR=#000000][FONT=Arial]Hi I have a Python script like this. I'm running it in Python version 3.4.2.[/FONT][/COLOR]
[COLOR=#00008B]import[/COLOR] csv
[COLOR=#00008B]import[/COLOR] sqlite3

[COLOR=#00008B]def[/COLOR] createTable(cursor, rows, tablename):
    tableCreated = [COLOR=#00008B]False[/COLOR]
    [COLOR=#00008B]for[/COLOR] row [COLOR=#00008B]in[/COLOR] rows:
        [COLOR=#00008B]if[/COLOR] [COLOR=#00008B]not[/COLOR] tableCreated:
            sql = [COLOR=#800000]"CREATE TABLE %s(ROW INTEGER PRIMARY KEY, "[/COLOR] + [COLOR=#800000]", "[/COLOR].join([[COLOR=#800000]"c%d"[/COLOR] % (i+[COLOR=#800000]1[/COLOR]) [COLOR=#00008B]for[/COLOR] i [COLOR=#00008B]in[/COLOR] range(len(row))]) + [COLOR=#800000]")"[/COLOR]
            cur.execute(sql % tablename)
            tableCreated = [COLOR=#00008B]True[/COLOR]
        sql = [COLOR=#800000]"INSERT INTO %s VALUES(NULL, "[/COLOR] + [COLOR=#800000]", "[/COLOR].join([[COLOR=#800000]"'"[/COLOR] + c + [COLOR=#800000]"'"[/COLOR] [COLOR=#00008B]for[/COLOR] c [COLOR=#00008B]in[/COLOR] row]) + [COLOR=#800000]")"[/COLOR]
        cur.execute(sql % tablename)
    conn.commit()


conn = sqlite3.connect([COLOR=#800000]":memory:"[/COLOR])
cur = conn.cursor()

[COLOR=#00008B]for[/COLOR] filename, tablename [COLOR=#00008B]in[/COLOR] [([COLOR=#800000]"in1.csv"[/COLOR], [COLOR=#800000]"CSV1"[/COLOR]), ([COLOR=#800000]"out1.csv"[/COLOR], [COLOR=#800000]"CSV2"[/COLOR])]:
    [COLOR=#00008B]with[/COLOR] open(filename, [COLOR=#800000]"r"[/COLOR]) [COLOR=#00008B]as[/COLOR] f:
        reader = csv.reader(f, delimiter=[COLOR=#800000]','[/COLOR])
        rows = [row [COLOR=#00008B]for[/COLOR] row [COLOR=#00008B]in[/COLOR] reader]
    createTable(cur, rows, tablename)

sql = [COLOR=#800000]"""WITH
MATCHES AS(SELECT      CSV2.*
                , CSV1.ROW as ROW_1                 
                , CSV1.C4 as C4_1
                , CSV1.C5 as C5_1
    FROM        CSV2 
    LEFT JOIN   CSV1 
    ON          CSV1.C4 LIKE '%' || CSV2.C2 || '%'    
),
EXACT AS(CSV1.C4 = CSV1.C5
    SELECT      *
    FROM        MATCHES
    WHERE       C4_1 = C5_1
),
MIN_ROW AS(SELECT      C1
                , min(ROW_1) as ROW_1
    FROM        MATCHES
    WHERE       C1 NOT IN (SELECT C1 FROM EXACT)
    GROUP BY    C1, C2, C3, C4, C5                  
)
SELECT      *
FROM        EXACT
UNION
SELECT      MATCHES.*
FROM        MIN_ROW
INNER JOIN  MATCHES
ON          MIN_ROW.C1 = MATCHES.C1
AND         (MIN_ROW.ROW_1 = MATCHES.ROW_1 OR MIN_ROW.ROW_1 IS NULL)
ORDER BY    C1"""[/COLOR]
[COLOR=#00008B]for[/COLOR] row [COLOR=#00008B]in[/COLOR] cur.execute(sql):
    [COLOR=#00008B]print[/COLOR] (row)[COLOR=#000000][FONT=Arial]Running this script gives me[/FONT][/COLOR]
[COLOR=#2B91AF]Traceback[/COLOR] (most recent call [COLOR=#00008B]last[/COLOR]):
  [COLOR=#2B91AF]File[/COLOR] [COLOR=#800000]"script.py"[/COLOR], line [COLOR=#800000]55[/COLOR], [COLOR=#00008B]in[/COLOR] [COLOR=#800000]<module>[/COLOR]
    [COLOR=#00008B]for[/COLOR] row [COLOR=#00008B]in[/COLOR] cur.execute(sql):
sqlite3.[COLOR=#2B91AF]OperationalError[/COLOR]: near [COLOR=#800000]"CSV1"[/COLOR]: syntax error[COLOR=#000000][FONT=Arial]I've been working on this script for quite some time now and I'm totally lost. I'd really appreciate if anyone could get me out of this with a working script. Please find the below sample CSV files.
in1.csv
[/FONT][/COLOR]
```
[COLOR=#222222][FONT=Verdana]Homo sapiens,Vertebrate Taxonomy Ontology,direct,Homo sapiens,Homo sapiens,Vertebrate Taxonomy Ontology[/FONT][/COLOR]Homo sapiens,Systematized Nomenclature of Medicine - Clinical Terms,direct,Homo sapiens,Homo sapiens,Systematized Nomenclature of Medicine - Clinical Terms
Homo,Vertebrate Taxonomy Ontology,direct,Homo sapiens,Homo,Vertebrate Taxonomy Ontology



```out1.csv
```
!Sample_title, !Sample_geo_accession, !Sample_status, !Sample_type, !Sample_source_name_ch1, !Sample_organism_ch1, !Sample_characteristics_ch1, !Sample_characteristics_ch1, !Sample_characteristics_ch1, !Sample_characteristics_ch1, !Sample_characteristics_ch1, !Sample_characteristics_ch1, !Sample_molecule_ch1, !Sample_extract_protocol_ch1, !Sample_label_ch1, !Sample_label_protocol_ch1, !Sample_hyb_protocol, !Sample_scan_protocol, !Sample_description, !Sample_data_processing, !Sample_platform_id
PBMC_S.aureus_MSSA_INF005, GSM173178, Public on march 16 2007, ribonucleic acid, PBMC_S. aureus, Homo sapiens, Age: 10 years- when sample taken, Gender: male, Race: Hispanic, Illness:  Osteomyelitis, Treatment: Cefazolin, Pathogen: S. aureus- MSSA, total ribonucleic acid, RNeasy mini, biotin, Biotinylated complementary rna were prepared according to the standard Affymetrix protocol., Standard Affymetrix protocol., GeneChips were scanned using the Agilent GeneArray 2500 Scanner., The subject was infected with S. aureus- MSSA., The data were analyzed with Microarray Suite version 5.0 (meconium aspiration syndrome 5.0) using Affymetrix default analysis settings and global scaling as normalization method. The trimmed mean target intensity of each array was arbitrarily set to 500., GPL96
PBMC_S.pneumoniae_INF009, GSM173179, Public on march 16 2007, ribonucleic acid, PBMC_S. pneumoniae, Homo sapiens, Age:4 months- when sample taken, Gender: male, Race: Caucasian, Illness:  Abscess, Treatment: Cefazolin, Pathogen: S. pneumoniae, total ribonucleic acid, RNeasy mini, biotin, Biotinylated complementary rna were prepared according to the standard Affymetrix protocol., Standard Affymetrix protocol., GeneChips were scanned using the Agilent GeneArray 2500 Scanner., The subject was infected with S. pneumoniae., The data were analyzed with Microarray Suite version 5.0 (meconium aspiration syndrome 5.0) using Affymetrix default analysis settings and global scaling as normalization method. The trimmed mean target intensity of each array was arbitrarily set to 500., GPL96

```

---

