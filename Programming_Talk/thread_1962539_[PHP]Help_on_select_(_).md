---
title: "[PHP]Help on select ( )"
date: 2012-04-21
forum: Programming Talk
---

### Post by kenweill on 2012-04-21
On my website script, there's this code

[PHP]
$coupons = $data->select ( "Coupon" , "*" , array ( "WebsiteID" => intval ( $website["WebsiteID"] ) , "IsApproved" => 1 ) , 0 , 150 , "DateAdded desc" ) ;
[/PHP]

It fetches data on mysql database with conditions and order by DateAdded.

Changing the "DateAdded desc" to "DateTested desc" changed the order by "DateTested".

Now, I wanted to change it to both.

First priority, order by DateTested.
Second priority, all others will be order by DateAdded.
I wonder how to do it. I wonder what part of that code should I change or add.

I tried "DateTested DateAdded desc" to no avail.
I also tried "DateTested desc", "DateAdded desc" to no avail. Probably it's more than the number of arguments the select () can have.

Anybody knows how to sort them by DateTested first and all others, order by DateAdded?

Thanks in advance.

Found the select class on site:
[PHP]
		function select ( $table , $selectWhat = "*" , $where = NULL , $start = -1 , $limit = 15 , $orderBy = "" )
		{
			if ( $table == "" )
			{
				$this->errorString = "Table not found." ;
				return NULL ;
			}
			if ( $orderBy != "" )
			{
				$orderBy = " order by " . $orderBy ;
			}
			
			$connection = Database::connect ( ) ;
			$query = "select $selectWhat from $table where 1 " ;
			if ( is_array ( $where ) && $where != NULL )
			{
				if ( ! empty ( $where ) )
				{
					foreach ( $where as $key=>$val )
					{
						if ( $val == NULL )
							$query .= " and $key is null " ;
						else
							$query .= " and $key='$val' " ;
					}
				}
			}
			if ( ! empty ( $this->like_array ) )
			{
				$operator = "and" ;
				foreach ( $this->like_array as $key => $val )
				{
					$query .= " $operator $key like '%".$val."%'" ;
					$operator = "or" ;
				}
			}
			$this->like_array = NULL ;
			
			if ( ! empty ( $this->greater_array ) )
			{
				foreach ( $this->greater_array as $key => $val )
					$query .= " and $key < $val" ;
			}
			$this->greater_array = NULL ;
			
			if ( ! empty ( $this->smaller_array ) )
			{
				foreach ( $this->smaller_array as $key => $val )
					$query .= " and $key >= $val" ;
			}
			$this->smaller_array = NULL ;
			
			if ( $this->group_by != "" )
				$query .= "group by ".$this->group_by ;
			$query .= $orderBy ;
			$records = Database::get_record_set ( $query ) ;
			$this->numberOfRecords = Database::get_total_records ( ) ;
			if ( $start > -1 )
			{
				$records = Database::get_record_set ( $query." limit $start, $limit" ) ;
			}
			else
			{
				$records = Database::get_record_set ( $query." limit 20" ) ;
			}
			
			return Database::records_to_array ( $records ) ;
		}
[/PHP]

This might help.

---

### Post by kenweill on 2012-04-21
Problem fixed with "DateTested desc, DateAdded desc"

Thanks for the PM.

---

