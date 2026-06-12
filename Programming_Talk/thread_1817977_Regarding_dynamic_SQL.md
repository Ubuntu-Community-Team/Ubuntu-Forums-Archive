---
title: "Regarding dynamic SQL"
date: 2011-08-04
forum: Programming Talk
---

### Post by vjohnny8 on 2011-08-04
I want to make the below query dynamic

/*needs to be dynamic*/
alter table c2c_bk_man_filetype 
add (
date_format varchar2(8) default 'DDMMYY' not null
, date_start_pos int default 0 not null
)
;

It should be in the below format.

set feedback off;
set define off;
set serveroutput on;
declare
v_table_name varchar2(50);
v_col_name varchar2(50);
v_count number(2);
v_sql varchar2(1000);
begin

v_table_name := 'C2C_BK_MAN_FILETYPE';
v_col_name := 'FILE_PARAMETERS';

select count(*) into v_count 
from user_tab_columns t
where lower(t.TABLE_NAME) = lower('C2P_ETL_BATCH_CONFIG')
and lower(t.COLUMN_NAME) = lower('FILE_PARAMETERS');

if v_count > 0 then
v_sql := 'alter table '||v_table_name||' modify FILE_PARAMETERS VARCHAR2(250) default ' ' not null';
execute immediate v_sql;
dbms_output.put_line('Column '||v_col_name|| ' of the table '||v_table_name||' is modified'); 
else
dbms_output.put_line('Column '||v_col_name|| ' is not present in the table '||v_table_name);
end if;

end;
/

set feedback on
set define on

how can i do it ?

---

