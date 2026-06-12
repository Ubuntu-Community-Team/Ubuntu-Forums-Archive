---
title: "SQL Search Query"
date: 2012-03-28
forum: Programming Talk
---

### Post by Brooksy_FC on 2012-03-28
I've got a SQL database set up on a LAMP server and I've got some a table with some data, things like names, ages and locations. 

I want to be able to have a search engine type thing so users can search a name/age/ or location and details come up.

For example, if they search "21" it will list the people who are 21.

I've got a HTML page set up so I need it needs to be view able on there.

Thanks in advance.

---

### Post by CynicRus on 2012-03-28
```
SELECT * FROM table_name WHERE (union) [order by field_name [desc][asc]]
```Searching stored procedure for mysql:
```
DROP PROCEDURE IF EXISTS find_overall;
delimiter $$
CREATE PROCEDURE find_overall(
  p_dbname VARCHAR(64),
  p_search VARCHAR(255)
)
BEGIN
  DECLARE query TEXT;
  DECLARE eof BOOL;
  DECLARE curs_tables CURSOR FOR
    SELECT CONCAT(
        'SELECT "', c.table_name, '" `$table$`, ', GROUP_CONCAT(
          CONCAT(
            'SUM(IF(`', c.column_name, '` LIKE "%%", 1, 0))',
            ' `', c.column_name, '`'
          )
          SEPARATOR ', '
        ),
        ' FROM `', c.table_schema, '`.`', c.table_name, '`'
        ' WHERE ', GROUP_CONCAT(
          CONCAT('`', c.column_name, '`')
          SEPARATOR ' LIKE "%%" OR '
        ), ' LIKE "%%"'
      ) query
    FROM information_schema.columns c
    WHERE c.table_schema = p_dbname
      AND c.data_type IN (
        'char', 'varchar', 'binary', 'varbinary',
        'tinytext', 'text', 'mediumtext', 'longtext',
        'tinyblob', 'blob', 'mediumblob', 'longblob'
      )
    GROUP BY c.table_name;
  DECLARE CONTINUE HANDLER FOR NOT FOUND SET eof = TRUE;

  OPEN curs_tables;
  SET eof = FALSE;

  L_tables: LOOP
    FETCH curs_tables INTO query;

    IF eof THEN LEAVE L_tables; END IF;

    SET @stm = REPLACE(query, '"%%"',
      CONCAT('"%', REPLACE(p_search, "'", "\\'") , '%"')
    );
    PREPARE find_overall FROM @stm;
    EXECUTE find_overall;
    DROP PREPARE find_overall;
  END LOOP;

  CLOSE curs_tables;
END;$$
delimiter ;
```

---

