# sql



select


/*	Maximum value from columns on the same row	*/

,	(select max (v) from  (values (##COLUMN_1##), (##COLUMN_2##),  (##COLUMN_3##)) as  value (v))  as  'max_##COLUMN##_at'


/*  Timezone UTC to local as datetime */

, cast  (##COLUMN## at  time  zone  'UTC' at  time  zone  'GMT Standard Time' as  datetime) as  '##COLUMN##_at'


/*  Pivot via sum + case  */

, sum (case when  ##COLUMN##  = '##'  then  1 else  0 end)  as  'count_##COLUMN##'


/*  Concatenate multiple columns with a delimeter without null values  */

,	concat_ws	(';',	##COLUMN_1##,	##COLUMN_2##,	##COLUMN_3##,	##COLUMN_4##,	##COLUMN_5##)	as	'##COLUMN##'
