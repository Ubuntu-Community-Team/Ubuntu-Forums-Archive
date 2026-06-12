---
title: "PHP Trouble displaying array"
date: 2010-09-23
forum: Programming Talk
---

### Post by k33bz on 2010-09-23
I am having a problem displaying dates (Month, Day, Year) from a drop down menu. Instead of displaying jan feb mar etc etc, or 2010, 2009, or anything I am seeing nothing but {name}.

Image is attached below of what I mean.

/lib/forms.php
```

<?php

define ("_MSG_FORMS_UNCOMPLETE" , "Please fill in all required fields");

define ("_MSG_FORMS_UNIQUE" , " already exists.");

define ("_MSG_FORMS_FILEEXISTS" , " doesn't exists.");

$form_months = array (1 => "January" , "February" , "March" , "April" , "May" , "June" , "July" , "August" , "September" , "October" , "November" , "December");



$form_US_states = array (

							"AL" => "Alabama",

							"AK" => "Alaska",

							"AZ" => "Arizona",

							"AR" => "Arkansas",

							"CA" => "California",

							"CO" => "Colorado",

							"CT" => "Connecticut",

							"DE" => "Delaware",

							"DC" => "Dist. of Columbia",

							"FL" => "Florida",

							"GA" => "Georgia",

							"HI" => "Hawaii",

							"ID" => "Idaho",

							"IL" => "Illinois",

							"IN" => "Indiana",

							"IA" => "Iowa",

							"KS" => "Kansas",

							"KY" => "Kentucky",

							"LA" => "Louisiana",

							"ME" => "Maine",

							"MD" => "Maryland",

							"MA" => "Massachusetts",

							"MI" => "Michigan",

							"MN" => "Minnesota",

							"MS" => "Mississippi",

							"MO" => "Missouri",

							"MT" => "Montana",

							"NE" => "Nebraska",

							"NV" => "Nevada",

							"NH" => "New Hampshire",

							"NJ" => "New Jersey",

							"NM" => "New Mexico",

							"NY" => "New York",

							"NC" => "North Carolina",

							"ND" => "North Dakota",

							"OH" => "Ohio",

							"OK" => "Oklahoma",

							"OR" => "Oregon",

							"PA" => "Pennsylvania",

							"PR" => "Puerto Rico",

							"RI" => "Rhode Island",

							"SC" => "South Carolina",

							"SD" => "South Dakota",

							"TN" => "Tennessee",

							"TX" => "Texas",

							"UT" => "Utah",

							"VT" => "Vermont",

							"VA" => "Virginia",

							"WA" => "Washington",

							"WV" => "West Virginia",

							"WI" => "Wisconsin",

							"WY" => "Wyoming"

						);



$form_countries = array(

							"AF" => "Afghanistan",

							"AL" => "Albania",

							"DZ" => "Algeria",

							"AS" => "American Samoa",

							"AD" => "Andorra",

							"AO" => "Angola",

							"AQ" => "Antartica",

							"AG" => "Antiqua and Barbuda",

							"AM" => "Armenia",

							"AR" => "Argentina",

							"AU" => "Australia",

							"AT" => "Austria",

							"AZ" => "Azerbaijan",

							"BS" => "Bahamas, The",

							"BH" => "Bahrain",

							"BD" => "Bangladesh",

							"BB" => "Barbados",

							"BY" => "Belarus",

							"BE" => "Belgium",

							"BZ" => "Belize",

							"BJ" => "Benin",

							"BM" => "Bermuda",

							"BT" => "Bhutan",

							"BO" => "Bolivia",

							"BW" => "Botswana",

							"BV" => "Bouvet Island",

							"BR" => "Brazil",

							"BQ" => "British Antartic Territory",

							"IO" => "British Indian Ocean Territory",

							"SB" => "British Solomon Islands",

							"VG" => "British Virgin Islands",

							"BN" => "Brunei",

							"BG" => "Bulgaria",

							"MM" => "Burma",

							"BI" => "Burundi",

							"KH" => "Cambodia",

							"CM" => "Cameroon",

							"CA" => "Canada",

							"CT" => "Canton and Enderbury Islands",

							"CV" => "Cape Verde Islands",

							"KY" => "Cayman Islands",

							"CF" => "Central African Republic",

							"TD" => "Chad",

							"CL" => "Chile",

							"CN" => "China, People's Republic of",

							"CX" => "Christmas Island",

							"CC" => "Cocos (Keeling) Islands",

							"CO" => "Colombia",

							"KM" => "Comoro Islands",

							"CG" => "Congo",

							"CK" => "Cook Islands",

							"CR" => "Costa Rica",

							"HR" => "Croatia",

							"CU" => "Cuba",

							"CY" => "Cyprus",

							"CZ" => "Czech Republic",

							"DY" => "Dahomey",

							"DK" => "Denmark",

							"DJ" => "Djibouti",

							"DM" => "Dominica",

							"DO" => "Dominican Republic",

							"NQ" => "Dronning Maud Land",

							"EC" => "Ecuador",

							"EG" => "Egypt",

							"SV" => "El Salvador",

							"GQ" => "Equitorial Guinea",

							"ER" => "Eritrea",

							"EE" => "Estonia",

							"ET" => "Ethiopia",

							"FO" => "Faeroe Islands",

							"FK" => "Falkland Islands (Malvinas)",

							"FJ" => "Fiji",

							"FI" => "Finland",

							"FR" => "France",

							"GF" => "French Guiana",

							"PF" => "French Polynesia",

							"FQ" => "French South and Antartic Territory",

							"AI" => "French Afars and Issas",

							"GA" => "Gabon",

							"GM" => "Gambia",

							"GE" => "Georgia",

							"DE" => "Germany",

							"GH" => "Ghana",

							"GI" => "Gibraltar",

							"GR" => "Greece",

							"GL" => "Greenland",

							"GD" => "Grenada",

							"GP" => "Guadeloupe",

							"GU" => "Guam",

							"GT" => "Guatemala",

							"GN" => "Guinea",

							"GW" => "Guinea Bissaw",

							"GY" => "Guyana",

							"HT" => "Haiti",

							"HM" => "Heard and McDonald Islands",

							"HN" => "Honduras",

							"HK" => "Hong Kong",

							"HU" => "Hungary",

							"IS" => "Iceland",

							"IN" => "India",

							"ID" => "Indonesia",

							"IR" => "Iran",

							"IQ" => "Iraq",

							"IE" => "Ireland",

							"IL" => "Israel",

							"IT" => "Italy",

							"CI" => "Ivory Coast",

							"JM" => "Jamaica",

							"JP" => "Japan",

							"JT" => "Johnston Island",

							"JO" => "Jordan",

							"KZ" => "Kazakhstan",

							"KE" => "Kenya",

							"KH" => "Khmer Republic",

							"KP" => "Korea, Democratic People's Republic of",

							"KR" => "Korea, Republic of",

							"KW" => "Kuwait",

							"KG" => "Kyrgystan",

							"LA" => "Laos",

							"LV" => "Latvia",

							"LB" => "Lebanon",

							"LS" => "Lesotho",

							"LR" => "Liberia",

							"LY" => "Libya",

							"LI" => "Liechtenstein",

							"LT" => "Lithuania",

							"LU" => "Luxembourg",

							"MO" => "Macao",

							"MG" => "Madagascar",

							"MW" => "Malawi",

							"MY" => "Malaysia",

							"MV" => "Maldives",

							"ML" => "Mali",

							"MT" => "Malta",

							"MH" => "Marshall Islands",

							"MQ" => "Martinique",

							"MR" => "Mauritania",

							"MU" => "Mauritius",

							"MX" => "Mexico",

							"FM" => "Micronesia",

							"MI" => "Midway Islands",

							"MD" => "Moldova",

							"MC" => "Monaco",

							"MN" => "Mongolia",

							"MS" => "Montserrat",

							"MA" => "Morocco",

							"MZ" => "Mozambique",

							"MM" => "Myanmar (formerly Burma)",

							"NA" => "Namibia",

							"NR" => "Nauru",

							"NP" => "Nepal",

							"NL" => "Netherlands",

							"AN" => "Netherlands Antilles",

							"NT" => "Neutral Zone",

							"NC" => "New Caledonia",

							"NH" => "New Hebrides",

							"NZ" => "New Zealand",

							"NI" => "Nicaragua",

							"NE" => "Niger",

							"NG" => "Nigeria",

							"NU" => "Niue Island",

							"NF" => "Norfolk Island",

							"NO" => "Norway",

							"OM" => "Oman",

							"PC" => "Pacific Island Trust Territory",

							"PK" => "Pakistan",

							"PW" => "Palau",

							"PA" => "Panama",

							"PZ" => "Panama Canal Zone",

							"PG" => "Papua New Guinea",

							"PY" => "Paraguay",

							"PE" => "Peru",

							"PH" => "Philippines",

							"PN" => "Pitcairn Islands",

							"PL" => "Poland",

							"PT" => "Portugal",

							"TP" => "Portuguese Timor",

							"PR" => "Puerto Rico",

							"QA" => "Qatar",

							"RE" => "Reunion Island",

							"RO" => "Romania",

							"RU" => "Russia",

							"RW" => "Rwanda",

							"SH" => "St. Helena",

							"KN" => "St. Kitts-Nevis-Anguilla",

							"LC" => "St. Lucia",

							"PM" => "St. Pierre and Miquelon",

							"VC" => "St. Vincent",

							"SM" => "San Marino",

							"ST" => "Sao Tome and Principe",

							"SA" => "Saudi Arabia",

							"SN" => "Senegal",

							"SC" => "Seychelles",

							"SL" => "Sierra Leone",

							"SG" => "Singapore",

							"SK" => "Slovakia",

							"SI" => "Slovenia",

							"SO" => "Somalia",

							"ZA" => "South Africa, Republic of",

							"ES" => "Spain",

							"EH" => "Spanish Sahara",

							"LK" => "Sri Lanka",

							"SD" => "Sudan",

							"SR" => "Suriname",

							"SJ" => "Svalbard and Jan Mayen Islands",

							"SZ" => "Swaziland",

							"SE" => "Sweden",

							"CH" => "Switzerland",

							"SY" => "Syria",

							"TW" => "Taiwan",

							"TJ" => "Tajikistan",

							"TZ" => "Tanzania",

							"TH" => "Thailand",

							"TG" => "Togo",

							"TK" => "Tokelau Island",

							"TO" => "Tonga",

							"TT" => "Trinidad and Tobago",

							"TN" => "Tunisia",

							"TR" => "Turkey",

							"TM" => "Turkmenistan",

							"TC" => "Turks and Caicos Islands",

							"TV" => "Tuvalu",

							"UG" => "Uganda",

							"UA" => "Ukraine",

							"AE" => "United Arab Emirates",

							"GB" => "United Kingdom",

							"US" => "United States",

							"PU" => "U.S. Miscellaneous Pacific Islands",

							"VI" => "U.S. Virgin Islands",

							"HV" => "Upper Volta",

							"UY" => "Uruguay",

							"UZ" => "Uzbekistan",

							"VU" => "Vanuatu",

							"VA" => "Vatican City State (The Holy See)",

							"VE" => "Venezuela",

							"VN" => "Vietnam",

							"WK" => "Wake Island",

							"WF" => "Wallis and Futuna Islands",

							"WS" => "Western Samoa",

							"YE" => "Yemen",

							"YD" => "Yemen, Democratic",

							"YU" => "Yugoslavia",

							"ZR" => "Zaire",

							"ZM" => "Zambia",

							"ZW" => "Zimbabwe"

						);



class CForm extends CLibrary{



	/**

	* description

	*

	* @var type

	*

	* @access type

	*/

	var $db;



	/**

	* description array with all functions to be executed in various posittions in cform

	*

	* @var type

	*

	* @access type

	*/

	var $functions;

	



	/**

	* description

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function CForm($template , $db , $tables , $form = "") {

		parent::CLibrary("CForm");



		//adding extra check if the file is a template or is a string		

		if (!is_object($template)) {			

			$template = new CTemplate($template);

		}



		//optionaly added $form

		$this->form = $this->Process($form);



		$this->templates = $template;

		$this->db = $db;

		$this->tables = $tables;



	}



	/**

	* description checking if the input is an array or an xml file 

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function Process($input) {

		if (is_array($input)) {

			return $input;

		} else {

			if (file_exists($input)) {

				$xml = new CConfig($input);				

				$xml->vars["form"]["xmlfile"] = $input ;



				return $xml->vars["form"];

			} else

				return null;			

		}		

	}

	

	/**

	* description

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function ProcessLinks($link) {

		return CryptLink($link);

	}

	

	/**

	* description

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function Validate($form  , $input) {



		$form = $this->Process($form);





		if (is_array($form)) {



			foreach ($form["fields"] as $key => $val)

	

				if ($val["validate"] && $val["required"] && !$val["hidden"])

					$_valid_temp[] = strtoupper($val["name"] ? $val["name"] : $key) . ":" . $val["validate"];



			$validate = @implode("," , $_valid_temp);

			

		}				

		

		//validate the input fields

		$result = ValidateVars($input ,$validate);

		$vars = array();



		if (is_array($result)) {

		

			foreach ($result as $key => $val)

				$fields["errors"][strtolower($val)] = 1;



			$fields["error"] = _MSG_FORMS_UNCOMPLETE;

			$fields["values"] = $input;



		} else {



			//proceed to complex validation for unique fields 

			if (is_array($form)) {

				

				foreach ($form["fields"] as $key => $val) {

		

					if ($val["unique"] == "true") {



						//check if this is an adding processor or editing one

						if ($input[$form["table_uid"]]) {

							$old_record = $this->db->QFetchArray("SELECT * FROM `" . $this->tables[$form["table"]] . "` WHERE `" . $form["table_uid"] . "`='" . $input[$form["table_uid"]] . "'" );

						}



						$name = $val["name"] ? $val["name"] : $key ;

						$data = $this->db->QFetchArray("SELECT `$name` FROM `" . $this->tables[$form["table"]] . "` WHERE `" . $name . "` = '" . $input[$name] . "'");



						if (((is_array($data) && is_array($old_record)) && ($data[$name] != $old_record[$name])) || (is_array($data) && !is_array($old_record))) {



							//preparing the message

							$fields["error"] = $val["unique_err"] ? $val["unique_err"] : $val["title"] . _MSG_FORMS_UNIQUE;

							$fields["errors"][$name] = 1;

							$fields["values"] = $input;



						}

					}



					// search to see if is a vvalid file path

					if ($val["fileexists"] == "true") {

						$name = $val["name"] ? $val["name"] : $key ;



						if (!is_file($input[$name])) {

							//preparing the message

							$fields["error"] = $val["fileexists_err"] ? $val["fileexists_err"] : $val["title"] . ": \"$input[$name]\"" . _MSG_FORMS_FILEEXISTS;

							$fields["errors"][$name] = 1;

							$fields["values"] = $input;

						}

						

					}



					// search to see if is a vvalid file path

					if (($val["type"] == "password") && !strstr($key , "_confirm")) {

						$name = $val["name"] ? $val["name"] : $key ;



						if ($input[$name] != $input[$name . "_confirm"]) {

							//preparing the message

							$fields["error"] = "Password and confirmation doesnt match.";

							$fields["errors"][$name] = 1;

							$fields["errors"][$name . "_confirm"] = 1;

							$fields["values"] = $input;

						}

						

					}



				}

					

			}

			

		}



		return is_array($fields) ? $fields : true;



	}



	/**

	* description

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function SimpleList($form , $items = "", $count = "", $extra = null , $search = false) {

		global $_CONF;



		//if i got no elements from preloader functions, then i load it manualy

		if (!is_array($items)) {



			//cheking if is a normal browse or a search method

			if ($search) {



				$items = $this->db->QuerySelectLimit($this->tables[$form["table"]],"*", "`" . $_GET["what"] . "` " . ( $_GET["type"] == "int" ? "='" . $_GET["search"] . "'" : "LIKE '%" . $_GET["search"] . "%'"),(int) $_GET["page"],$form["items"]);

				$count = $this->db->RowCount($this->tables[$form["table"]] , " WHERE `" . $_GET["what"] . "` " . ( $_GET["type"] == "int" ? "='" . $_GET["search"] . "'" : "LIKE '%" . $_GET["search"] . "%'"));



			} else {



			}

		}



		if (is_array($form["vars"])) {

			foreach ($form["vars"] as $key => $val) {

				//echeking if the default must be evaluated

				if ($val["action"] == "eval") {

					eval("\$val[\"import\"] = " . $val["default"] .";");

				}



				switch ($val["type"]) {

					case "eval":

						eval("\$tpl_vars[\"$key\"] = " . $val["import"] . ";");

					break;



					case "var":

						$tpl_vars[$key] = $val["import"];

					break;

				}													

			}

		}



		//add an extra element to vars

		$tpl_vars["current_page"] = urlencode(urlencode($_SERVER["REQUEST_URI"]));



		if (is_array($form["sql"])) {



			if (is_array($form["sql"]["vars"])) {

				foreach ($form["sql"]["vars"] as $key => $val) {

					//echeking if the default must be evaluated

					if ($val["action"] == "eval") {

						eval("\$val[\"import\"] = " . $val["default"] .";");

					}



					switch ($val["type"]) {

						case "eval":

							eval("\$sql_vars[\"$key\"] = " . $val["import"] . ";");

						break;



						case "var":

							$sql_vars[$key] = $val["import"];

						break;



						case "page":

							$sql_vars[$key] = ($_GET[($val["code"] ? $val["code"] : 'page')] -1 )* $form['items'];

						break;



						case "form":

							eval("\$sql_vars[\"$key\"] = " . $form[$val["var"]] . ";");

						break;



					}													

				}



				foreach ($sql_vars as $key => $val) {							

					$this->templates->blocks["Temp"]->input = $val;							

					$sql_vars[$key] = $this->templates->blocks["Temp"]->Replace($sql_vars);

				}	



				//doing a double replace, in case there are unreplaced variable sfom "vars" type

				$this->templates->blocks["Temp"]->input = $form["sql"]["query"];

				$sql = $this->templates->blocks["Temp"]->Replace($sql_vars);



				//do a precheck for [] elements to be replaced with <>

				$sql = str_replace("]" , ">" , str_replace("[" , "<" , $sql));

				$items = $this->db->QFetchRowArray($sql);

				//$items = $this->Query						



				//processing the counting query

				if (is_array($form["sql"]["count"])) {



					//if no table is set then i use the default table'

					$form["sql"]["count"]["table"] = $form["sql"]["count"]["table"] ? $form["sql"]["count"]["table"] : $form["table"];



					foreach ($form["sql"]["count"] as $key => $val) {

						$this->templates->blocks["Temp"]->input = $val;							

						$form["sql"]["count"][$key] = $this->templates->blocks["Temp"]->Replace($sql_vars);

					}						



					$count = $this->db->RowCount($form["sql"]["count"]["table"] , $form["sql"]["count"]["condition"] , $form["sql"]["count"]["select"]);

				}

				

			}



			

		} else {				

			if (!is_array($items)) {	

				$items = $this->db->QuerySelectLimit($this->tables[$form["table"]],"*","",(int) $_GET["page"],$form["items"]);

				$count = $this->db->RowCount($this->tables[$form["table"]]);

			}

		}



		$_GET["page"] = $_GET["page"] ? $_GET["page"] : 1;

		//auto index the element

		$start = $form["items"] * ($_GET["page"] ? $_GET["page"] - 1 : 0);



		if (is_array($items)) {

			foreach ($items as $key => $val) {

				$items[$key]["_count"] = ++$start;

			}			

		}		



		$html = new CHtml();



		$form = $this->Process($form);



		$template = &$this->templates;



		//this sux, building the template

		if (is_array($form["fields"])) {

			foreach ($form["fields"] as $key => $val) {

				$data .= $template->blocks["ListCell"]->Replace (

							array (

								"width" => $val["width"],

								"align" => $val["align"],

								"value" => "{" . strtoupper($key) . "}"

							)

						  );



				//buildint the title header

				$titles .= $template->blocks["ListTitle"]->Replace ( array(

																		"title" => ($val["header"] ?  $val["header"]  : "&nbsp"),

																		"width" => $val["width"]



																	));

			}



			//adding one more title col in titles ( the one for buttons )

			$titles .= $template->blocks["ListTitle"]->Replace ( array("title" => "&nbsp" ));



			$row = $data . $template->blocks["ButtonsCell"]->output;



			$template->blocks["ListElement"]->input = $template->blocks["ListRow"]->Replace(array("ROW"=> $row ));

			$titles = $template->blocks["ListRow"]->Replace(array("ROW"=> $titles ));



			// i know this is stupid, but now i dont have other idees

			//if i see a variable <no heade> then i clear the template

			if ($form["header"]["titles"] == "false") {

				$titles = "";

			}

			

		}

		

		//bulding the header buttons and search box

		if (is_array($form["header"]["buttons"])) {

			foreach ($form["header"]["buttons"] as $key => $val) {

				$val = array_merge($_GET , $val);



				$this->templates->blocks["Temp"]->input = $val["location"];

				$val["location"] = $this->templates->blocks["Temp"]->Replace($val);

				$val["location"] = CryptLink($val["location"]);

				$header["buttons"] .= $template->blocks["Button"]->Replace($val);

			}					

		}



		// the search options, this is kinda buggy for this version, will be fixed in other

		if (is_array($form["header"]["search"])) {

			$form_search = $form["header"]["search"];



			//bulding the droplist options

			if (is_array($form_search["options"])) {



				foreach ($form_search["options"] as $key => $val) {

					$search_form[$key]["label"] = $val;

					$search_form[$key]["checked"] = $_GET[$form_search["variable"]] == $key ? " selected " : "";

				}

				

				

				$search["droplist"] = $html->FormSelect(

											"what" , 

											$search_form ,

											$template,

											"Select" ,

											$_GET["what"],

											$search_form ,

											array(	

												"width" => "" ,

												"onchange" => ""

											)

									);				



				//building the form and the buttons

				//reading all varibals from $_GET excepting the $_GET["page"], and transform them in hidden fields

				if (is_array($_GET)) {

					$temp = $_GET;



					//force the action variable

					$temp[$this->forms["uridata"]["action"]] = $this->forms["uridata"]["search"];



					foreach ($temp as $key => $val) {

						if (!in_array($key , array( "page" , "what" , "search")))  {

							

							$search["fields"] .= $template->blocks["SearchField"]->Replace(array("name" => $key , "value" => $val));

						}						

					}					

				}



				//preparing the action, post the requests to the same file as curernt

				$search["action"] = $_SERVER["PHP_SELF"];

				$search["value"] = $_GET["search"];



				$header["search"] = $template->blocks["SearchForm"]->Replace($search);				

			}

		}



		//checking if header exists, then add the template

		if (is_array($header) || $form["subtitle"] || $form["header"]["titles"]) {



			//cleanup the variables

			$header["buttons"] = $header["buttons"] ? $header["buttons"] : "";

			$header["search"] = $header["search"] ? $header["search"] : "";

			$header["subtitle"] = $form["subtitle"];



			//building the template

			$header = $template->blocks["ListHeader"]->Replace($header);



			$template->blocks["ListGroup"]->input = $template->blocks["ListGroup"]->Replace(array(

														"_HEADER" => $header , 

														"_TITLES" => $titles ,

														//adding the extra html

														"_HTML_PRE" => (is_array($form["html"]["pre"]) && ($form["html"]["pre"]["type"] == "extern")) ? GetFileContents(dirname($form["xmlfile"]) . "/" . $form["html"]["pre"]["file"]) : html_entity_decode($form["html"]["pre"]),

														"_HTML_MIDDLE" => (is_array($form["html"]["middle"]) && ($form["html"]["middle"]["type"] == "extern")) ? GetFileContents(dirname($form["xmlfile"]) . "/" . $form["html"]["middle"]["file"]) : html_entity_decode($form["html"]["middle"]),

														"_HTML_AFTER" => (is_array($form["html"]["after"]) && ($form["html"]["after"]["type"] == "extern")) ? GetFileContents(dirname($form["xmlfile"]) . "/" . $form["html"]["after"]["file"]) : html_entity_decode($form["html"]["after"]),



														"PRE" => $extra["pre"],

														"AFTER" => $extra["after"]

													));

		} else {

			//cleanup the vars

			$form["_HEADER"] = "";

			$form["_TITLES"] = "";

			$form["_HTML_PRE"] = "";

			$form["_HTML_AFTER"] = "";

			$form["pre"] = $form["after"] = "";

		}



		//prereplace the vars main template

		$template->blocks["ListGroup"]->input = $template->blocks["ListGroup"]->Replace($form);



		//prereplace the pagination template



		if (is_array($_GET)) {

			foreach ($_GET as $key => $val) {

				if ($key != "page")

				$url[] = "$key=$val";

			}

			

			$url = $_SERVER["SCRIPT_NAME"] . "?" . @implode("&" , $url) . "&";

		}



		$template->blocks["Page"]->input = $template->blocks["Page"]->Replace(array("BASE" => $url));

		

		$_GET["page"] = ($_GET["page"] ? $_GET["page"] : "1");



		//preprocessing the items

		if (is_array($items)) {

			foreach ($items as $key => $val) {

				if (is_array($form["fields"])) {



					foreach ($form["fields"] as $k => $v) {

						switch ($v["type"]) {



							case "date":



								if (isset($val[$k . "_day" ]) && isset($val[$k . "_month" ]) && isset($val[$k . "_year" ]))  {



									$items[$key][$k] = 

														( $val[$k . "_month" ] ? sprintf("%02d" ,$val[$k . "_month" ])  : "--" ). "." . 

														( $val[$k . "_day" ] ? sprintf("%02d" ,$val[$k . "_day" ]) : "--" ) . "." .  

														( $val[$k . "_year" ] ? $val[$k . "_year" ] : "----" ) ;

								} else						

									//$field["value"] = $field["value"] > 0 ? @date($field["params"] , $field["value"]) : "not available";

									$items[$key][$k] = $items[$key][$k] > 0 ? @date($v["params"] , ($v["now"] == "true" ? time() : $items[$key][$k])) : "N/A";



//								$items[$key][$k] = $items[$key][$k] > 0 ? @date($v["params"] , ($v["now"] == "true" ? time() : $items[$key][$k])) : "N/A";

							break;



							case "price":

								$items[$key][$k] = number_format($items[$key][$k],2);

							break;



							case "image":

								if ($items[$key][$k]) {

									// if is the image then show it

									$items[$key][$k] = $template->blocks["imageshow"]->Replace(

															array(

																"width" => $v["width"],

																"height" => $v["height"],

																"src" => $_CONF["url"] . $_CONF["upload"] . $v["path"] . $v["file"]["default"] . $items[$key][$v["file"]["field"]] . $v["file"]["ext"]

															)

														);

								} else {

									//else check if the default image exists

									if ($v["default"]) {

										$items[$key][$k] = $template->blocks["imageshownolink"]->Replace(

																array(

																	"width" => $v["width"],

																	"height" => $v["height"],

																	"src" => $_CONF["url"] . $_CONF["upload"] . $v["path"] . $v["default"]

																)

															);

									} else 

										//if not simply return a space

										$items[$key][$k] = "&nbsp;";

								}

							break;



							case "relation":

								//cheking if there are static relations or dinamic relations

								if (is_array($v["options"])) {

									//ok, i have the static ones

									$items[$key][$k] = $v["options"][$items[$key][$k]] ? $v["options"][$items[$key][$k]] : "&nbsp;";	

								}

					

								if (is_array($v["relation"])) {

									//reading from database



									$sql =	"SELECT * FROM `" . $this->tables[$v["relation"]["table"]] . "` WHERE `" . $v["relation"]["id"] . "`='" . $items[$key][$k] . "'";



									$record =$this->db->QFetchArray( $sql );

									$items[$key][$k] = $record[$v["relation"]["text"]];



									//build the label for multiple fields 



									if (is_array($v["relation"]["text"])) {

										$_tmp_text = "";



										foreach ($v["relation"]["text"] as $kkey => $vval)

											$_tmp_text[] = $record[$vval];

										

										$items[$key][$k] = implode($v["relation"]["separator"] ? $v["relation"]["separator"] : " " , $_tmp_text);

									} else

										//else return the single field

										$items[$key][$k] = $record[$v["relation"]["text"]];



								}														

								

								

							break;



							default:

								$items[$key][$k] = $items[$key][$k] ? htmlentities(stripslashes($items[$key][$k])) : "&nbsp;";

							break;

						}							



						$items[$key][$k] = $v["preffix"] . ( strtoupper($v["allownl"]) == "TRUE" ? nl2br($items[$key][$k]) : $items[$key][$k] ). $v["suffix"];

					}

				}				



				//adding the ing buttons

				if (is_array($form["buttons"])) {

					foreach ($form["buttons"] as $key2 => $val2) {



						if ($key2 != "set") {

							//do a replace with the values from the item

							$this->templates->blocks["Temp"]->input = $val2["location"];						

							$val2["location"] = $this->ProcessLinks($this->templates->blocks["Temp"]->Replace(array_merge($items[$key],$tpl_vars)));



							//do an extra replacement for space with %20

							$val2["location"] = str_replace(" ","%20" , $val2["location"]);



							$items[$key]["buttons"] .= 

									($form["buttons"]["set"]["buttonsvert"] == "true" ? "<tr><td height=3></td></tr><tr>" : "" ). 

									$template->blocks["Button"]->Replace($val2) . 

									($form["buttons"]["set"]["buttonsvert"] == "true" ? "</tr>" : "" );

						}

					}				

				} else {

					$items[$key]["buttons"] = "";

				}



			}			

		}

		

		if ($form["items"]) {

			$return = $html->Table( $template , "List" , $items , true , $count , $form["items"] , $_GET["page"] , $template );

		} else {

			$return = $html->Table( $template , "List" , $items);

		}



		//crap, append some extra elements to this form, in case, , i dont know how to handle if there will be 2 pagging functions.



		if (is_array($this->functions["list"]["after"]))

			call_user_func($this->functions["list"]["after"],$append);



		//clearing the extra value

		if (!$append) {

			$append = "";

		}

		

		//adding the border



		//doing a small trick before adding the border

		if ($form["border"] != "true") {

			//overwrite the border template with the content one

			$template->blocks["Border"]->input = $return;

			//empty the return variable

			$return = "";

		}

		

		$return = $template->blocks["Border"]->Replace( 

					array(

						"_TEMPLATE_DATA" => $return , 

						"WIDTH" => $form["width"], 

						"TITLE" => $form["title"] , 

						"EXTRA" => $append

					));

		

		$this->templates->blocks["Temp"]->input = $return;

		return $this->templates->blocks["Temp"]->Replace($tpl_vars);



	}



	/**

	* description

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function InsertField( $params ) {

		//for the momment it dont support complex fields like referers, and multiple



		//preparing the input vars

		$form["fields"]["temp"] = $params;

		$values["values"][$params["name"]] = $params["value"] ;



		//draw the element

		return $this->DrawElement ( $form , "temp" , $values ); 

	}

	

	/**

	* description

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function privateDrawTree($field , $cats , $values , $parent = 0 , $level = 0, $sep = '') {



		

		$return = "";

		//if i found categories then return the list of it

		if (is_array($cats)) {



			$sep = preg_replace( 

							array( '(\[)' , '(\])' ),

							array( "<" , ">" ),

							$field["tree"]["separator"]

						);



			//prepare the values

			//do a small check to see if there are values set in separed values

			//preparing the separator

			if ($level > 0 ) {

				$separator = "";



				for ($i = 0; $i< $level; $i++) {

					$separator .= $sep;					

				}				

			}



			foreach ($cats as $key => $val) {



				if ($val[$field["tree"]["parent"]] == $parent) {			



					$return .= $this->templates->blocks["SelectTree" . ($field["editable"] == "false" ? "Disabled" : "" )]->Replace( 

										array (

											"LABEL" => $val[$field["tree"]["text"]],

											"ID" => $val[$field["tree"]["id"]],

											"NAME" => $field["name"],

											"CHECKED" => $values["values"][$field["name"] . "_option_" . $val[$field["tree"]["id"]]] ? ' checked="checked" ' : "",

											"X" => $values["values"][$field["name"] . "_option_" . $val[$field["tree"]["id"]]] ? 'x' : " ",

											"SEPARATOR" => $separator,

											"PARENT" => $val[$field["tree"]["parent"]]

										)

								);

																			

					$return .= $this->privateDrawTree($field , $cats , $values , $val[$field["tree"]["id"]], $level + 1 , $sep);

				}

			}			



			return $return;

		} else {

			return "";

		}



	}

	



	/**

	* description

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function DrawElement( $form , $_field , $values , $draw_referer = 0 ) {



		global $_CONF,$form_US_states,$form_countries;



		//some default settings

		$_textareaCols = 30;

		$_textareaRows = 4;



		$_textboxSize = 20;

		$_textboxMaxLength = "";



		$_textareaButtons = array (

				"1" => "'cut' ,  'copy' , 'paste' , 'separator' , 'undo' , 'redo' , 'separator' , 'removeformat' , 'toolbar' , 'bold' , 'italic' , 'underline' , 'strike' , 'superscript' , 'subscript' , 'insertorderedlist' , 'insertunorderedlist' , 'indent' , 'outdent' , 'inserthr'",

				"2" => "'font-family' , 'font-size' , 'justifyleft' ,  'justifycenter' , 'justifyright' , 'justifyfull'"

			);



		$field = $form["fields"][$_field];



		//doing a precheck in case there are referers or multiples to elements which arent in xml

		if (!is_array($field))

			return "";		



		if (!$field["type"]) {

			return "";

		}

		

		

		//a temporary solution for name loosing

		$field["name"] = $_field;



		if (!$values["values"][$field["name"]]) {		

			switch ($field["action"]) {

				case "eval":

					eval("\$field[\"value\"] = " . $field["default"] . ";");

				break;



				default:

					$field["value"]	= $field["default"];

				break;

			}

		} else {

			

			$field["value"] = $values["values"][$field["name"]];

		}

		

		//somtimes i may want to force a specific value nomatter of what is already set

		if (isset($field["forcevalue"])) {

			$field["value"] = $field["forcevalue"];

		}



		//load data from external files

		if ((($field["type"] != "image")&&($field["type"] != "upload")) && is_array($field["file"]) && !($values["values"][$field["name"]]) && file_exists($_CONF["path"] . $_CONF["upload"] . $field["file"]["path"] . $field["file"]["default"] . $values["values"][$field["file"]["field"]] . $field["file"]["ext"])) {

			$values["values"][$field["name"]] = stripslashes(GetFileContents($_CONF["path"] . $_CONF["upload"] . $field["file"]["path"] . $field["file"]["default"] . $values["values"][$field["file"]["field"]] . $field["file"]["ext"]));

		}		



		//strip the slashes from the value

//		$field["value"] = stripslashes($field["value"]);

			

		//checking if this file is a referer, and if i have to show the referers at this point

		if (! $draw_referer && (($field["referer"] == "true") || ($field["multiple"] == "true")))

			return "";



		//drawing the form elements

		switch ($field["type"]) {



			case "textarea":

				

				if (is_array($temp = @explode(":" , $field["size"]))) {

					//size from xml

					$field["_cols"] = $temp["0"];

					$field["_rows"] = $temp["1"];

				} else {

					//preset size

					$field["_cols"] = $_textareaCols;

					$field["_rows"] = $_textareaRows;

				}



				//uhm ... this is a crappy part becouse i have to integrate the html editor here so ...

				if ($field["html"] == "true") {

					//checking if the editor.js was loaded until now

					if ($_GLOBALS["cform_editor_loaded"] != true) {

						$current_field = $this->templates->blocks["htmlareainit"]->output;

						$_GLOBALS["cform_editor_loaded"] = true;

					}



					//checking if the buttons exists, else add the buttons from default

					if (!is_array($field["buttons"])) {

						$field["buttons"] = $_textareaButtons;

					}

					



					if (is_array($field["buttons"])) {

						$buttons = $field["buttons"];

						//clear the buttons from field, it will be rplaced with the template

						$field["buttons"] = "";



						foreach ($buttons as $k => $v) {

							$field["buttons"] .= $this->templates->blocks["htmlareabutton"]->Replace(

													array(

														"NAME" => $field["name"],

														"BUTTONS" => is_array($v) ? "" : $v

													)

												);

						}

					} else

						$field["buttons"] = "";



					$current_field .= $this->templates->blocks["htmlarea"]->Replace($field);

				} else {				

					$field["value"] = stripslashes(htmlentities($field["value"]));

					$current_field = $this->templates->blocks["textarea"]->Replace($field);

					//$current_field = $this->templates->blocks["textarea"]->EmptyVars();

				}



				//valign for forms which has more then one field

				$current_field_extra = $this->templates->blocks["TopAlign"]->output;

			break;



			case "file":				

				$field["file"] = $values["values"][$field["name"]];

				$this->templates->blocks["file"]->Replace($field , false);

				$current_field = $this->templates->blocks["file"]->EmptyVars();	

				

				//if the field hs description then i add the valign code

				$current_field_extra = $field["description"] ? $this->templates->blocks["TopAlign"]->output : ""; 

			break;



			case "password":

			case "textbox":

				

				//check if the size for textbox is defined

				if ($field["size"]) {



					//autodetect if the size value contaigns the maxlength too

					if (is_array($temp = @explode(":" , $field["size"]))) {								



						$field["_size"] = $temp["0"];

						$field["_maxlength"] = $temp["1"];



					} else {



						//else the size field is the size of textbox

						$field["_size"] = $field["size"];

						$field["_maxlength"] = $_textboxMaxLength;

					}



				} else {

					//get the default values



					$field["_size"] = $_textboxSize;

					$field["_maxlength"] = $_textboxMaxLength;

				}



				$field["value"] = stripslashes(htmlentities($field["value"]));



				$current_field = $this->templates->blocks[$field["type"]]->Replace($field);

				//$current_field = $this->templates->blocks[$field["type"]]->EmptyVars();	

				

				//if the field hs description then i add the valign code

				$current_field_extra = $field["description"] ? $this->templates->blocks["TopAlign"]->output : ""; 

			break;



			case "text":



				$field["value"] = $field["html"] == "true" ? stripslashes($field["value"]) : nl2br(stripslashes(htmlentities($field["value"])));



				switch ($field["action"]) {

					case "date":

						if (isset($values["values"][$field["name"] . "_day" ]) && isset($values["values"][$field["name"] . "_month" ]) && isset($values["values"][$field["name"] . "_year" ])) 

							$field["value"] = 

												( $values["values"][$field["name"] . "_month" ] ? sprintf("%02d" ,$values["values"][$field["name"] . "_month" ])  : "--" ). "." . 

												( $values["values"][$field["name"] . "_day" ] ? sprintf("%02d" ,$values["values"][$field["name"] . "_day" ]) : "--" ) . "." .  

												( $values["values"][$field["name"] . "_year" ] ? $values["values"][$field["name"] . "_year" ] : "----" ) ;

						else						

							$field["value"] = $field["value"] > 0 ? @date($field["params"] , $field["value"]) : "not available";

					break;



					case "price":

						$field["value"] = number_format($field["value"] , 2);

					break;

				}



				$current_field = $this->templates->blocks["text"]->Replace($field , false);

				//$current_field = $this->templates->blocks["text"]->EmptyVars();	



				//if the field hs description then i add the valign code

				$current_field_extra = $field["valign"] ? $this->templates->blocks["TopAlign"]->output : ""; 

			break;



			case "hidden":

				//fix a small bug, if the hidden!= true then the elemet is drow like normal element.

				$field["hidden"] = "true";

/*

				//crap some evals here too :)

				if ($values["values"][$field["name"]]) {

					$field["value"] = $values["values"][$field["name"]];

				} else {

					

					switch ($field["action"]) {

						case "eval":

							eval("\$field[\"value\"] = " . $field["default"] . ";");

						break;



						default:

							$field["value"] = $field["default"];

						break;

					}

				}								

*/				

				$current_field = $this->templates->blocks["hidden"]->Replace($field , false);

				//$current_field = $this->templates->blocks["hidden"]->EmptyVars();	

				$current_field_extra = "";

			break;



			case "button":			

				$current_field = $this->templates->blocks["button"]->Replace($field , false);

				//$this->templates->blocks["button"]->EmptyVars();							



				//if the field hs description then i add the valign code

				$current_field_extra = $field["description"] ? $this->templates->blocks["TopAlign"]->output : ""; 

			break;



			case "checkbox":

			

				$field["checked"] = $values["values"][$field["name"]] ? " checked=\"checked\" " : "";



				$this->templates->blocks["checkbox"]->Replace($field , false);

				$current_field = $this->templates->blocks["checkbox"]->EmptyVars();							



				//if the field hs description then i add the valign code

				$current_field_extra = $field["description"] ? $this->templates->blocks["TopAlign"]->output : ""; 

			break;



			case "USstates":								

			case "relation":

			case "droplist":

			case "countries":



				switch ($field["type"]) {

					case "USstates":

					case "states":

						$field["options"] = $form_US_states;

					break;



					case "countries":

						$field["options"] = $form_countries;

					break;



					case "relation":

						$field["editable"] = "false";

					break;

				}

				

				//clearign vals

				$temp_options = "";



				//check if the options are generated dinamic

				if (is_array($field["dynamic"])) {

					for ($i = $field["dynamic"]["from"]; $i<=$field["dynamic"]["to"]; $i++ ) {

						$field["options"][$i] = $field["dynamic"]["width"] ? sprintf("%0" . $field["dynamic"]["width"] . "d", $i) : $i;						

					}					

				}



				if (is_array($field["options"])) {



					//add the enpty option

					if ($field["empty"] == "true") {

						$temp_options = $this->templates->blocks["SelectOption"]->Replace(array(

																								"LABEL" => $field["empty_text"] ? $field["empty_text"] : "",

																								"VALUE" => "",

																								"DISABLED" => "",

																								"CHECKED" => ""																																																));

					}



					//building the select from options

					foreach ($field["options"] as $key => $val) {



						//hm ... support for noeditable fields, will apear as text

						if ($field["editable"] == "false") {

							foreach ($field["options"] as $key => $val) {

								if ($key == $values["values"][$field["name"]]) {



									$field["value"] = $val;



									$this->templates->blocks["text"]->Replace($field , false);

									$current_field = $this->templates->blocks["text"]->EmptyVars();	

								}							

							}						



						} else {					



							//checking if is a complex option or a simple one

							if (is_array($val)) {

								$label = $val["value"];

								$disabled = $val["disabled"] == "true" ? " disabled " : "";

							} else {

								$label = $val;

								$disabled = "";

							}

							

							$temp_options .= $this->templates->blocks["SelectOption"]->Replace(

												array(	

													"value" => $key,

													"label" => $label,

													"checked" => ($key == $values["values"][$field["name"]] ? " selected=\"selected\" " : ""),

													"disabled" => $disabled

												)

											  );

						}

					}														

				} else

					if (is_array($field["relation"])) {

						//reading from database

						

						//check to eval the condition if requred

						if (is_array($field["relation"]["condition"]) && ($field["relation"]["condition"]["eval"] == "true")) {

							echo "\$field[\"relation\"][\"condition\"] = " . $field["relation"]["condition"]["import"];

							eval("\$field[\"relation\"][\"condition\"] = " . $field["relation"]["condition"]["import"]);

						}

						

						$sql =	"SELECT * FROM `" . $this->tables[$field["relation"]["table"]] . "`" . 

								($field["relation"]["condition"] ? " WHERE (" . $field["relation"]["condition"] . ") " : "" ) . 

								($field["relation"]["order"] ? " ORDER BY `" . $field["relation"]["order"] . "` " . 

								($field["relation"]["ordermode"] ? $field["relation"]["ordermode"] : "") : "" );



						$records =$this->db->QFetchRowArray( $sql );



						//ckech and replace the label field with multi fields array

						if (is_array($tmp_fields = @explode($field["tree"]["db_separator"] , $values["values"][$field["name"]]))) {

							foreach ($tmp_fields as $_val) {

								$_tmp_fields[$_val] = $_val;

							}							

						}

							

						

						if (is_array($records)) {

							if ($field["subtype"] == "multiple") {

											

								foreach ($records as $_k => $_v) {

									if ($_tmp_fields[$_v[$field["tree"]["id"]]] == $_v[$field["tree"]["id"]])

										$values["values"][$field["name"]."_option_" . $_v[$field["tree"]["id"]]] = true;

								}



								$temp_options = $this->privateDrawTree($field, $records , $values);



								//check if the overflow div settings are enabled

								if (is_array($field["tree"]["div"])) {

									$temp_options = $this->templates->blocks["SelectDiv"]->Replace(array(

																										"WIDTH" => $field["tree"]["div"]["width"],

																										"HEIGHT" => $field["tree"]["div"]["height"],

																										"SELECT_DATA" =>$temp_options 

																									));

								}

								

								

								

							} else {



								//add the enpty option

								if ($field["empty"] == "true") {

									$temp_options = $this->templates->blocks["SelectOption"]->Replace(array(

																											"LABEL" => $field["empty_text"] ? $field["empty_text"] : "",

																											"VALUE" => "",

																											"DISABLED" => "",

																											"CHECKED" => ""

																										));

								}

								

								//echo "`" . $field["relation"]["id"] . "`"	;



								foreach ($records as $key => $val) {

									//preparing the data to send to template

									$send = array();

									$_tmp_text = "";



									$send["value"] = $val[$field["relation"]["id"]];

									$send["checked"] = $val[$field["relation"]["id"]] == $field["value"] ? " selected=\"selected\" " : "";

									$send["disabled"] = "";

									

									//build the label for multiple fields 

									if (is_array($field["relation"]["text"])) {

										foreach ($field["relation"]["text"] as $kkey => $vval)

											$_tmp_text[] = $val[$vval];

										

										$send["label"] = implode($field["relation"]["separator"] ? $field["relation"]["separator"] : " " , $_tmp_text);

									} else

										//else return the single field

										$send["label"] = $val[$field["relation"]["text"]];



									// if the type is relation of editable false, then search for the selected element.

									if (($val[$field["relation"]["id"]] == $field["value"]) && ($field["editable"] == "false")) {



										$field["value"] = $send["label"];

										$this->templates->blocks["text"]->Replace($field , false);

										$current_field = $this->templates->blocks["text"]->EmptyVars();	



										//quit the for 

										break;



									}								

									

									$temp_options .= $this->templates->blocks["SelectOption"]->Replace($send);

								}

							}

						}

					}

				if ($field["editable"] != "false") {

					if ($temp_options != "") {

							if ($field["subtype"] == "multiple") {



								$current_field = $temp_options;



							} else {

								//if there are options, build the select

								$current_field = $this->templates->blocks["Select"]->Replace(array(

														"name" => $field["name"] , 

														"options" => $temp_options ,

														"width" => $field["width"],

														"onchange" => $field["onchange"]

													));

							}

					} else 

						//else return a message, customizable from xml

						$current_field = $field["empty"] ? $field["empty"] : $this->templates->blocks["selectempty"]->output;

				} else {

					if ($temp_options != "") {

							if ($field["subtype"] == "multiple") {



								$current_field = $temp_options;

							}

					}

				}

				

				//if the field hs description then i add the valign code

				$current_field_extra = $field["description"] || $field["subtype"] ? $this->templates->blocks["TopAlign"]->output : ""; 



			break;



			case "upload":

				$file = true;

			case "image":

				if ($field["editable"] != "false") {



					//adding the editable area to form

					$field["web_checked"] = $values["values"][$field["name"] . "_radio_type"] ? "checked" : "";

					$field["client_checked"] = $values["values"][$field["name"] . "_radio_type"] ? "" : "checked";

					$field["web_link"] = $values["values"][$field["name"] . "_upload_web"] ? $values["values"][$field["name"] . "_upload_web"] : "http://";

					$field["file_name"] = $values["values"][$field["name"] . "_file"];



					$field["rem_disabled"] = $values["values"][$field["name"] . "_temp"] || $values["values"][$field["name"] . "_temp"] || $values["values"][$field["name"]] ? "" : "disabled";



					$image["editable"] = $this->templates->blocks[$file ? "uploadedit" : "imageedit"]->Replace($field);

				}	



				if ($file) {

					if (is_file($_CONF["path"] . $_CONF["upload"] . "tmp/" . $values["values"][$field["name"] . "_temp"])) {



						//show the ing image

						$image["preview"] = $this->templates->blocks["fileshow"]->Replace(

												array(

													"name" => $_CONF["url"] . $_CONF["upload"] . "tmp/" . $values["values"][$field["name"] . "_file"],

													"src" => $_CONF["url"] . $_CONF["upload"] . "tmp/" . $values["values"][$field["name"] . "_temp"] 

												)

											);



					} else {

						$file_name = $_CONF["path"] . $_CONF["upload"] . ($field["path"] ? $field["path"] : $field["file"]["path"]) . $field["file"]["default"] . $values["values"][$field["file"]["field"]] . $field["file"]["ext"];

						$file_url = $_CONF["url"] . $_CONF["upload"] . ($field["path"] ? $field["path"] : $field["file"]["path"]) . $field["file"]["default"] . $values["values"][$field["file"]["field"]] . $field["file"]["ext"];



						if (/*$values["values"][$field["name"]] && */file_exists($file_name)) {

							$image["preview"] = $this->templates->blocks["fileshow"]->Replace(

													array(

														"name" => $values["values"][$field["name"] . "_file"] ? $values["values"][$field["name"] . "_file"]  : $field["file"]["default"] . $values["values"][$field["file"]["field"]] . $field["file"]["ext"],

														"src" => $file_url

													)

												);

						} else 

							$image["preview"] = $field["error"] ? $field["error"] : "No file uploaded.";

					}



				} else {

				

					if (is_file($_CONF["path"] . $_CONF["upload"] . "tmp/" . $values["values"][$field["name"] . "_temp"])) {



						//show the ing image

						$image["preview"] = $this->templates->blocks["imageshow"]->Replace(

												array(

													"width" => $field["adminwidth"],

													"height" => $field["adminheight"],

													"src" => $_CONF["url"] . $_CONF["upload"] . "tmp/" . $values["values"][$field["name"] . "_temp"] 

												)

											);



					} else {



						//hm ... making a small trick to keep the image even if that was an failed adding,

						//this sux becouse if the add process is not completed then i get crap in the temp folder.					

						if ($values["values"][$field["name"]] && file_exists($_CONF["path"] . $_CONF["upload"] . $field["path"] . $field["file"]["default"] . $values["values"][$field["file"]["field"]] . $field["file"]["ext"])) {

							$image["preview"] = $this->templates->blocks["imageshow"]->Replace(

													array(

														"width" => $field["adminwidth"],

														"height" => $field["adminheight"],

														"src" => $_CONF["url"] . $_CONF["upload"] . $field["path"] . $field["file"]["default"] . $values["values"][$field["file"]["field"]] . $field["file"]["ext"]

													)

												);



						} else {



							//checking if there exists a default image

							if ($field["default"]) {

								$image["preview"] = $this->templates->blocks["imageshownolink"]->Replace(

														array(

															"width" => $field["adminwidth"],

															"height" => $field["adminheight"],

															"src" => $_CONF["url"] . $_CONF["upload"] . $field["path"] . $field["default"]

														)

													);

							} else

								//return an error from xml

								$image["preview"] = $field["error"] ? $field["error"] : "No image curently available.";

						}

					}

				}



				$image["temp"] = $values["values"][$field["name"] . "_temp"];

										

				$this->templates->blocks["image"]->Replace($image , false);

				$current_field = $this->templates->blocks["image"]->EmptyVars();							



				//if the field hs description then i add the valign code

				$current_field_extra = $field["description"] ? $this->templates->blocks["TopAlign"]->output : ""; 

			break;



			case "comment":

				if ($field["subtype"] == "extern") {

					$field["description"] = GetFileContents(dirname($form["xmlfile"]) . "/" . $field["file"]);

				} else {

				

					$field["description"] = preg_replace( 

									array( '(\[)' , '(\])' ),

									array( "<" , ">" ),

									$field["description"]

								);

				}

				//save the input 

				$old = $this->templates->blocks["Comment"]->input ;



				//do the replaces

				$this->templates->blocks["Comment"]->input = $this->templates->blocks["Comment"]->Replace(array(

																											"COMMENT" => $field["description"],

																											"PADDING" => $field["padding"] ? $field["padding"] : "0"

																											));								

				$this->templates->blocks["Comment"]->input = $this->templates->blocks["Comment"]->Replace($values["values"]);

				$this->templates->blocks["Comment"]->input = $this->templates->blocks["Comment"]->Replace($_GET);

				$current_field = $this->templates->blocks["Comment"]->Replace($_POST);



				//restore the template 

				$this->templates->blocks["Comment"]->input = $old;

				//do a few other replaces

				//if the field hs description then i add the valign code

//				$current_field_extra = $field["description"] ? $this->templates->blocks["TopAlign"]->output : ""; 

			break;



			case "date":



				if (is_array($field["fields"])) {



//					echo "<pre style=\"background-color:white\">";

//					print_r($field);

//					print_r($values["values"]);



					$html = new CHtml;



					//do some variables cleaning

					if (is_array($years))

						unset($years);

					if (is_array($days))

						unset($days);

					if (is_array($months))

						unset($months);



					



					$date_vals = &$values["values"][$field["name"]];



					if ($date_vals > 1000) {



						//setting the previous values

						$year_selected = isset($values["values"][$field["name"] ."_year"]) ? $values["values"][$field["name"] ."_year"] : @date("Y" , $date_vals );

						$month_selected = isset($values["values"][$field["name"] ."_month"]) ? $values["values"][$field["name"] ."_month"] : @date("n" , $date_vals );

						$day_selected = isset($values["values"][$field["name"] ."_day"]) ? $values["values"][$field["name"] ."_day"] : @date("j" , $date_vals );



						//crap, adding the time values too

						$hour_selected = isset($values["values"][$field["name"] ."_hour"]) ? $values["values"][$field["name"] ."_hour"] : @date("G" , $date_vals );

						$minute_selected = isset($values["values"][$field["name"] ."_minute"]) ? $values["values"][$field["name"] ."_minute"] : @date("i" , $date_vals );

						$second_selected = isset($values["values"][$field["name"] ."_second"]) ? $values["values"][$field["name"] ."_second"] : @date("s" , $date_vals );

						

					} else {



						$fld = $field["fields"];



						//setting the default value 						

						$year_selected = $fld["year"]["default"] == "now" ? date("Y") : $fld["year"]["default"];

						$month_selected = $fld["month"]["default"] == "now" ? date("n") : $fld["month"]["default"];

						$day_selected = $fld["day"]["default"] == "now" ? date("j") : $fld["day"]["default"];



						//crap, adding the time values too

						$hour_selected = $fld["hour"]["default"] == "now" ? date("G") : $fld["hour"]["default"];

						$minute_selected = $fld["minute"]["default"] == "now" ? date("i") : $fld["minute"]["default"];

						$second_selected = $fld["second"]["default"] == "now" ? date("s") : $fld["second"]["default"];						

					}



					foreach ($field["fields"] as $key => $val) {

						switch ($key) {

							case "year":

								if ($field["fields"]["year"]["empty"] == "true") {

									$years[0] = "--" ;

								}

								

								for ($i = $field["fields"]["year"]["from"] ; $i <= $field["fields"]["year"]["to"] ; $i++ )

									$years[$i] = $i;									



								$current_field .= $html->FormSelect(

																		$field["name"]."_year" , 

																		$years , 

																		$this->templates , 

																		"DateSelect", 

																		$year_selected , 

																		array() , 

																		array("DISABLED" => ($field["fields"]["year"]["editable"] == "false") ? "DISABLED" : "")									

																	);



								$current_field .= $val["separator"];

							break;



							case "day":

								if ($field["fields"]["day"]["empty"] == "true") {

									$days[0] = "--" ;

								}



								for ($i = 1 ; $i <= 31 ; $i++ )

									$days[$i] = sprintf("%02d",$i);



								$current_field .= $html->FormSelect(

																		$field["name"]."_day" , 

																		$days , 

																		$this->templates , 

																		"DateSelect", 

																		$day_selected,

																		array() , 

																		array("DISABLED" => ($field["fields"]["day"]["editable"] == "false") ? "DISABLED" : "")

																	);

								$current_field .= $val["separator"];

							break;



							case "month":

								if (($field["fields"]["month"]["empty"] == "true"))  {

									$months[0] = "--" ;

								}



								//importing the months from global

								global $form_months;



								if (is_array($months))

									$formmonths = array_merge($months, $form_months);

								else

									$formmonths = $form_months;



								//ehcking if the dates must apear like strings or numbers

								$current_field .= $html->FormSelect(

																		$field["name"]."_month" , 

																		$formmonths, 

																		$this->templates , 

																		"DateSelect", 

																		$month_selected,

																		array() , 

																		array("DISABLED" => ($field["fields"]["month"]["editable"] == "false") ? "DISABLED" : "")

																	);



								$current_field .= $val["separator"];

							break;



							case "hour":

								for ($i = 0; $i <= 23; $i++ )

									$hours[$i] = sprintf("%02d",$i);;									



								$current_field .= $html->FormSelect(

																		$field["name"]."_hour" , 

																		$hours , 

																		$this->templates , 

																		"DateSelect", 

																		$hour_selected , 

																		array() , 

																		array("DISABLED" => ($field["fields"]["hour"]["editable"] == "false") ? "DISABLED" : "")									

																	);



								$current_field .= $val["separator"];

							break;



							case "minute":

								for ($i = 0; $i <= 59; $i++ )

									$minutes[$i] = sprintf("%02d",$i);;									



								$current_field .= $html->FormSelect(

																		$field["name"]."_minute" , 

																		$minutes , 

																		$this->templates , 

																		"DateSelect", 

																		$minute_selected , 

																		array() , 

																		array("DISABLED" => ($field["fields"]["minute"]["editable"] == "false") ? "DISABLED" : "")									

																	);



								$current_field .= $val["separator"];

							break;



							case "second":

								for ($i = 0; $i <= 59; $i++ )

									$seconds[$i] = sprintf("%02d",$i);;									



								$current_field .= $html->FormSelect(

																		$field["name"]."_second" , 

																		$seconds , 

																		$this->templates , 

																		"DateSelect", 

																		$second_selected , 

																		array() , 

																		array("DISABLED" => ($field["fields"]["minute"]["editable"] == "false") ? "DISABLED" : "")									

																	);



								$current_field .= $val["separator"];

							break;



						}						

					}					

				}				



				//if the field hs description then i add the valign code

				$current_field_extra = $field["description"] ? $this->templates->blocks["TopAlign"]->output : ""; 



			break;



			case "multiple":

				//cheking for multiple ellements

				

				if (is_array($field["multiple"])) {

					foreach ($field["multiple"] as $key => $val) {

						$current_field .= $this->DrawElement($form , $key , $values , 1);

					}					

				}

				$current_field_extra = $field["description"] ? $this->templates->blocks["TopAlign"]->output : ""; 

			break;



		}



		if ($field["hidden"] != "true") {



			//checking if this element isnt a referer

			if ($field["referer"] != "true") {



				//building the element structure ( title, description, etc )				

				$element["title"] = $field["title"];



				//replacing ]n with <br> in descriptions

				$field["description"] = $field["description"] ? nl2br(html_entity_decode(str_replace("]" , ">" , str_replace("[" , "<" , $field["description"])))) : null;

				$element["_description"] = $field["description"] ? $this->templates->blocks["Description"]->Replace($field) : "";

				$element["_description_rowspan"] = $field["description"] ? $this->templates->blocks["DescriptionRowspan"]->output : "";

				

				$element["_element"] = $current_field;



				//cheking if this element has referers

				

				if (is_array($field["referers"])) {

					foreach ($field["referers"] as $key => $val) {

						$element["_element"] .= "<td>" . $this->DrawElement($form , $key , $values , 1) . "</td>";

					}



					$element["_element"] = "<table><tr><td>" . $element["_element"] . "</tr></table>";

				}



				//adding the preffix and suffix

				$element["_suffix"] = $field["suffix"];

				$element["_preffix"] = $field["preffix"];

								

				$element["_extra"] = $current_field_extra;

				$element["_extra_code"] = $field["_extra_code"];



				$element["_required"] = $field["required"] == "true" ? trim($this->templates->blocks["RequiredMark"]->output) : "";

				$element["_required_error"] = $values["errors"][$field["name"]] ? trim($this->templates->blocks["Required"]->output) : "";



				//start with alternance empty;

				$element["_alternance"] = "";





				if (($field["multiple"] == "true") && $draw_referer ){

						return $this->templates->blocks["ElementMultipleBody"]->Replace($element);

				}



				if ($field["type"] == "multiple") {

					if ($form["alternance"] == "true") {

						$this->_tmpAlternance = $this->_tmpAlternance ? 0 : 1;

						$vars["_alternance"] = $this->templates->blocks["Alternance" . $this->_tmpAlternance]->output;



						$this->templates->blocks["Temp"]->input = $this->templates->blocks["ElementMultiple"]->Replace($element);

						return $this->templates->blocks["Temp"]->Replace($vars);

					} else					

						return $this->templates->blocks["ElementMultiple"]->Replace($element);

				}

				



				if ($field["extend"] != "true") {



					//do a smal trick for alternance colors

					if ($form["alternance"] == "true") {

						$this->_tmpAlternance = $this->_tmpAlternance ? 0 : 1;

						$vars["_alternance"] = $this->templates->blocks["Alternance" . $this->_tmpAlternance]->output;



						$this->templates->blocks["Temp"]->input = $this->templates->blocks["Element"]->Replace($element);

						return $this->templates->blocks["Temp"]->Replace($vars);

					} else {





						switch ($field["type"]) {

							case "subtitle":

								return $this->templates->blocks["Subtitle"]->Replace($element);

							break;



							case "comment":

								return $current_field;

							break;



							default:

								return $this->templates->blocks["Element"]->Replace($element);

							break;

						}

					}

				}

				else

					return $this->templates->blocks["ExtendElement"]->Replace($element);

			} else {

	

				//if the element is only a referer return only the form

				return $draw_referer ? $current_field : "";

			}



		} else {

			return $current_field;

		}



	}

	

		

	/**

	* description

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function Show($form , $values = array()  , $extra = array()) {

		global $_CONF;



		$form = $this->Process($form);



		//values structure

		/*

			<values>

				<error>Field already exists</error>



				<fields>

					<name>jon doe</name>

					<address>eartch </earth>

					...



				</fields>

			</values>

		*/



		if (is_array($form["vars"])) {

			foreach ($form["vars"] as $key => $val) {

				//echeking if the default must be evaluated

				if ($val["action"] == "eval") {

					eval("\$val[\"import\"] = " . $val["default"] .";");

				}



				switch ($val["type"]) {

					case "eval":

						eval("\$tpl_vars[\"$key\"] = " . $val["import"] . ";");

					break;



					case "var":

						$tpl_vars[$key] = $val["import"];

					break;

				}													

			}



		}



		if (is_array($form["fields"])) {

			foreach ($form["fields"] as $key => $field) {



				//checking for <code> field

				if (!$field["name"])

					$form["fields"][$key]["name"] = $key;

		

				//empty some variable for each field

				$element = array();

				$current_field_extra = "";

				$current_field = "";



				//do a precheck for values, to load it from _POST, _GET _SESSION _FILE _COOKIE

				if (!@isset($values["values"][$field["name"]]) && @isset($GLOBALS[$field["get"]][$field["name"]]))  {

					$values["values"][$field["name"]] = $GLOBALS[$field["get"]][$field["name"]];

				}



				$form["fields"][$key]["_extra_code"] = $extra["fields"][$key];

				$form["_template_data"] .= $this->DrawElement($form , $key, $values);

			}

		}



		//adding the ing buttons

		if (is_array($form["buttons"])) {

			foreach ($form["buttons"] as $key => $val)

				//checking not to be a setting group

				if ($key != "set") {



					//making a small trick to replace some vars in links, i hate this

					$this->templates->blocks["Temp"]->input = $val["location"];

					//replacing the values

					//also replaging the global variables defined for templates

					$this->templates->blocks["Temp"]->input = $this->templates->blocks["Temp"]->Replace($tpl_vars);



					$val["location"] = $this->templates->blocks["Temp"]->Replace($values["values"]);

					$val["location"] = CryptLink($val["location"]);

					$buttons .= $this->templates->blocks["Button"]->Replace($val);

				}



			$form["_header_buttons"] = $form["buttons"]["set"]["header"] == "true" ? $this->templates->blocks["HeaderButtons"]->Replace(array(

																																				"SUBTITLE" => ($form["subtitle"] ? $form["subtitle"] : "&nbsp;") , 

																																				"BUTTONS" => $buttons)) : "";



			$form["_footer_buttons"] = $form["buttons"]["set"]["footer"] == "true" ? $this->templates->blocks["FooterButtons"]->Replace(array("BUTTONS" => $buttons)) : "";

		} else {

			//return empty variable

			$form["_header_buttons"] = $form["_footer_buttons"] = "";

		}



		//check and add the error message

		if ($values["error"])

			$form["_error"] = $this->templates->blocks["Error"]->Replace(array("error" => $values["error"] ));		

		else

			$form["_error"] = "";



		//adduing the javascript to form

		$form["_pre_javascript"] = $form["javascript"]["pre"] ? "<script language=\"Javascript\">" . $form["javascript"]["pre"] . "</script>" : "";

		$form["_after_javascript"] = $form["javascript"]["after"] ? "<script language=\"Javascript\">" . $form["javascript"]["after"] . "</script>" : "";

		

		//adding the extra html

		$form["_pre_html"] = (is_array($form["html"]["pre"]) && ($form["html"]["pre"]["type"] == "extern")) ? GetFileContents(dirname($form["xmlfile"]) . "/" . $form["html"]["pre"]["file"]) : html_entity_decode($form["html"]["pre"]);

		$form["_middle_html"] = (is_array($form["html"]["middle"]) && ($form["html"]["middle"]["type"] == "extern")) ? GetFileContents(dirname($form["xmlfile"]) . "/" . $form["html"]["middle"]["file"]) : html_entity_decode($form["html"]["middle"]);

		$form["_after_html"] = (is_array($form["html"]["after"]) && ($form["html"]["after"]["type"] == "extern")) ? GetFileContents(dirname($form["xmlfile"]) . "/" . $form["html"]["after"]["file"]) : html_entity_decode($form["html"]["after"]);



		//adding the pre extra and after extra

		$form["_pre_form"] = $extra["pre"];

		$form["_after_form"] = $extra["after"];



		//preprocess the post form

		//replace the form vars in the form action

		$this->templates->blocks["Temp"]->input = $form["action"];

		$form["action"] = CryptLink($this->templates->blocks["Temp"]->Replace($tpl_vars));



		//drawing the form

		$form["_template_data"] = $this->templates->blocks["Form"]->Replace($form);



		//adding the <form tag

		if ($form["formtag"] == "true") {

			$form["id"] = $form["id"] ? " id=\"" . $form["id"] . "\" " : "";

			$form["encoding"] = $form["encoding"] ? $form["encoding"] : "";

			$form["method"] = $form["method"] ? $form["method"] : "post";

			$form["_template_data"] = $this->templates->blocks["Action"]->Replace( $form );

		}



		//adding the border

		if ($form["border"] == "true")

			$form["_template_data"] = $this->templates->blocks["Border"]->Replace( $form );



		if (is_array($form["vars"])) {

			//doing a double replace, in case there are unreplaced variable sfom "vars" type

			$this->templates->blocks["Temp"]->input = $form["_template_data"];

			$form["_template_data"] = $this->templates->blocks["Temp"]->Replace($tpl_vars);

		}

		



		return $form["_template_data"] ;

		

	}

}

?>


```

---

### Post by baddog144 on 2010-09-23
This belongs [here]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

### Post by dtfinch on 2010-09-24
It might also help to link to the full source code, like the chtml class that generates the the select dropdowns.
A google search led me to: [http://scripts.ringsworld.com/financial-tools/property-management-software/lib/html.php.html](http://scripts.ringsworld.com/financial-tools/property-management-software/lib/html.php.html) , though the bug is not immediately apparent to me.

---

### Post by k33bz on 2010-09-24
Here is all the scripts that I found that deal with chtml within this program. These are only snippits of the code since they are big.

You already see the lines up above in /lib/forms.php
They will be lines:
Starting at line 619
Starting at line 1591

/lib/site.php
line 90
```
		$base->html = new CHtml();
```

/lib/html.php
"sorry the whole script is defined as the code for class CHTML"
```

<?php

class CHTML {

	/**

	* generates paging from user data

	*

	* @param mixed $template	template file or object to work w/

	* @param int $ic			total number of items

	* @param int $ipp			items per page

	* @param int $cp			current page

	* @param array $vars		template vars [if any]

	* @param bool $pn			also include prev/next controls? [defaults to TRUE]

	*

	* @return string html page code

	*

	* @access public

	*/

	function Paging($template,$ic,$ipp,$cp,$vars,$pn = TRUE) {

		if ($ipp == 0) 

			return "";



		// check to see if paging required

		if ($ic > $ipp) {

			// init vars

			$result = "";



			// load template

			if (!is_object($template)) {

				$template = new CTemplate($template);

			}



			// set some helper templates

			$tpl_normal = $template->blocks["Page"];

			$tpl_active = $template->blocks["PageActive"];



			// compute page count

			$pc = round(ceil($ic / $ipp));



			// validate page

			if ($cp < 1)

				$cp = 1;

			elseif ($cp > $pc)

				$cp = $pc;



			// iterate thru all the pages

			for ($i = 0; $i < $pc; $i++) {

				// increment zerobased iterator

				$pn = $i + 1;



				// build template and make clickable if needed

				$tpl = ($pn == $cp) ? $tpl_active : $tpl_normal;



				// fill vars

				$vars["PAGE"] = $pn;

				$vars["FACE"] = $pn;



				// replace vars and add to result

				$result .= $tpl->Replace($vars);

			}



			// build prev/next

			if ($pn == TRUE) {

				// check if first page

				if ($cp > 1) {

					// fill vars

					$vars["PAGE"] = $cp - 1;

					$vars["FACE"] = $template->blocks["Prev"]->output;



					// replace vars and prepend to result

					$result = $tpl_normal->Replace($vars) . $result;

				}



				// check if last page

				if ($cp < $pc) {

					// fill vars

					$vars["PAGE"] = $cp + 1;

					$vars["FACE"] = $template->blocks["Next"]->output;



					// replace vars and append to result

					$result .= $tpl_normal->Replace($vars);

				}

			}



			// add the extra info and the pages to the result

			$return["ITEM_COUNT"] = $ic;

			$return["CURRENT_PAGE"] = $cp;

			$return["PAGE_COUNT"] = $pc;

			$return["PAGES"] = $result;



			// return the result

			return $template->blocks["Main"]->Replace($return);

		} else

			return "";

	}



	/**

	* dinamically generates a select form element w/ the provided data

	*

	* @param string $name		tag name attribute

	* @param array $vars		array of option values in the form of "VAL" => "NAME"

	* @param object $template	template object to use for generation

	* @param string $block		name of template block which contains the select body

	* @param string $selected	selected item if any [defaults to void]

	* @param array	$extra_vars	extra variables to be replaced in each option [keys must be

	*							the same of $vars to work properly]

	* @param array	$global_vars extra variables to be replaced in select

	*

	* @return string generated html code

	*

	* @access public

	*/

	function FormSelect($name,$vars,$template,$block,$selected = "",$extra_vars = array(), $global_vars = array()) {



		if (is_array($vars))

			foreach ($vars as $key => $val) {

				$replace = array(

					"VALUE" => $key,

					"NAME" => $val,

					"SELECTED" => (($key == $selected) ? " selected=\"selected\"" : "")

				);

				

				if (is_array($extra_vars))

					$replace = array_merge($replace,$extra_vars[$key]);



				$options .= $template->blocks["{$block}Option"]->Replace($replace);

			}



		if (count($global_vars) != 0)

			$select = $global_vars;

		$select["NAME"] = $name;

		$select["OPTIONS"] = $options;



		return $template->blocks["$block"]->Replace($select);

	}



	/**

	* description generating a custom seeting page from a template

	*

	* @param string $rights		a string contaign all rights

	* @param object $template	template object to use for generation

	* @param array $vars		variable with data :]

	*

	* @return string generated html code

	*

	* @access public

	*/

	function SettingsPage($template,$rights,$vars) {



		if (!$rights)

			return null;		



		$_rights = explode (",",$rights);

		$section = "NONE";		

		

		foreach ($_rights as $right) {

			// building an array with all sections

			if (strstr($right , "SEPARATOR") && is_object($template->blocks[$right] ))

				$SECTIONS[] = $section = $right;

			// buildin an array with sections data (templates)

			if (is_object($template->blocks["Section_" . $right]))

				$CONTENT[$section][] = $template->blocks["Section_" . $right]->Replace($vars);							

		}

		foreach ($SECTIONS as $SECTION) {

			// showing the section header if exists

			$return .= ($SECTION != "NONE") ? $template->blocks["Separator"]->Replace(array("CONTENT"=>$template->blocks[$SECTION]->output)) : "";

			$i = 0;

			while ($i < count($CONTENT[$SECTION])) {

				// showing block 2 by 2

				$content_1 = ($CONTENT[$SECTION][$i] ? $CONTENT[$SECTION][$i] : "<img width=0 height=0>");

				$content_2 = ($CONTENT[$SECTION][$i + 1] ? $CONTENT[$SECTION][$i + 1] : "<img width=0 height=0>");



				$return .= $template->blocks["Content"]->Replace(array("SECTION_1" => $content_1 , "SECTION_2" => $content_2 ));



				$i+= 2;

			}

		}



		return $template->blocks["Main"]->Replace(array("SECTIONS_CONTENT" => $return));

	}



	/**

	* description

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function Table($template,$template_block,$data,$has_paging = FALSE,$element_count = 0,$elements_per_page = 0,$page = 0,$paging_template = NULL,$paging_vars = array()) {



		if (is_array($data))

			foreach ($data as $element) {

				$element["date"] = @date("F j, Y, g:i a",$element["date"]);

				//echo "<br>" . $template_block . "Element";

				$return .= $template->blocks[$template_block . "Element"]->Replace($element);

			}

		else

			$return = $template->blocks[$template_block . "Empty"]->output;



		if ($has_paging == TRUE)

			$paging = $this->Paging($paging_template,$element_count,$elements_per_page,$page,$paging_vars);



		return $template->blocks[$template_block . "Group"]->Replace(array("DATA" => $return, "PAGING" => $paging));

	}



	/**

	* description

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function TableSimple($template,$block,$items,$vars = array(),$filler_func = NULL,$paging = NULL,$page = 0,$tic = 0,$paging_vars = array()) {

		$item_count = count($items);



		if (is_array($items)) {

			foreach ($items as $item) {

				if (is_array($filler_func) && is_array($item))

					call_user_func($filler_func,$item);

				$rows .= $template->blocks["{$block}Row"]->Replace($item);

			}

		} else

			$rows = $template->blocks["{$block}Empty"]->output;



		// setup paging

		$_paging = ($paging != NULL) ? $this->Paging($paging,$tic,$item_count,$page,$paging_vars) : "";



		// return the built layout

		return $template->blocks[$block]->Replace(array_merge(array("ROWS" => $rows, "PAGING" => $_paging),$vars));

	}



	/**

	* uses the specified data array to build a very simple table

	*

	* @param object	$template	template to use

	* @param string	$block		template block to use

	* @param array	$data		data array to be processed

	*

	* @return mixed the table or void if empty data

	*

	* @access public

	*/

	function TableLight($template,$block,$data) {

		if ($data == "")

			return "";

		else {

			foreach ($data as $item)

				$rows .= $template->blocks["{$block}Row"]->Replace($item);



			return $template->blocks[$block]->Replace(array("ROWS" => $rows));

		}

	}



	/**

	* builds and displays a multi row/col html table

	*

	* @param mixed $template	template file name or object

	* @param string $block		template block which contains the table body

	* @param array $items		array w/ the table items

	* @param int $rc			row count

	* @param int $cc			column count

	* @param array $vars		array of variables to be replaced in block [if needed]

	* @param mixed $filler_func	array of object and method to call for filling other vars in the item

	* @param mixed $paging		template filename or object used for paging [defaults to NULL]

	* @param int $page			current `page'

	* @param int $tic			total item count [used for paging]

	* @param array $paging_vars	array of vars to be replaced in the paging templates

	*

	* @return string html code of the built table

	*

	* @access public

	*/

	function TableComplex($template,$block,$items,$rc,$cc,$vars = array(),$filler_func = NULL,$paging = NULL,$page = 0,$tic = 0,$paging_vars = array()) {

		// compute item count ?

		$item_count = count($items);



		// if we have any items we proceed

		if (is_array($items)) {

			// recompute row/column count

			$row_count = ceil(count($items) / $cc);

			$column_count = ceil(count($items) / $row_count);



			// setup the column and row data

			$columns = "";

			$rows = "";



			// and the position in the data array

			$key = 0;



			// iterate thru all the rows

			for ($i = 0; $i < $row_count; $i++) {

				// iterate thru all the row`s columns

				for ($j = 0; $j < $column_count; $j++) {

					// set our current item

					$item = $items[$key];



					// then feed it to the filler func if needed

					if (is_array($filler_func) && is_array($item))

						call_user_func($filler_func,$item);



					// populate column data + check if the cell is empty

					$columns .= (is_array($item)) ? $template->blocks["Column"]->Replace($item) : $template->blocks["ColumnEmpty"]->output;



					// increment the position in the data array

					$key++;

				}



				// populate the row data and reset the column data to prepare it for the next row

				$rows .= $template->blocks["Row"]->Replace(array("COLUMNS" => $columns));

				$columns = "";

			}

		} else

			// we dont have any items so we handle it gracefully

			$rows = $template->blocks["Empty"]->output;

		// setup paging

		$_paging = ($paging != NULL) ? $this->Paging($paging,$tic,$item_count,$page,$paging_vars) : "";



		// return the built layout

		return $template->blocks[$block]->Replace(array_merge(array("ROWS" => $rows, "PAGING" => $_paging),$vars));

	}



	/**

	* description

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function error($template,$id) {

		return $template->blocks[$id]->output;

	}



}

?>



```

---

### Post by ibuclaw on 2010-09-24
You want people to look through how many lines of code?

Try getting your problem down to a minimised test case, and then report back if you still don't understand why it is going wrong. Though the chances am, you'll figure out where you are going wrong in the process of reducing your code.

---

### Post by ibuclaw on 2010-09-24
Reopening after chat with OP.

---

### Post by k33bz on 2010-09-24
> **ibuclaw said:**
> Reopening after chat with OP.


Thank you ibuclaw

---

### Post by Maheriano on 2010-09-24
Use a more descriptive thread title, that doesn't tell us anything and it's annoying to see such generic titles.

I know what your problem is but you'll have to provide a shorter piece of code so I can point it out exactly. I can't go through 1000 lines.

---

### Post by k33bz on 2010-09-24
> **Maheriano said:**
> Use a more descriptive thread title, that doesn't tell us anything and it's annoying to see such generic titles.

I know what your problem is but you'll have to provide a shorter piece of code so I can point it out exactly. I can't go through 1000 lines.

Understandable, just tell me what I am looking for so I can provide a better and smaller snippet to narrow it down to post.

I am working on /lib/forms.php to see I cant cut out the bs, make it single space, and try to narrow down the particular arrays involved. Cant guarantee that it will be that much smaller.

MODS, CAN YOU PLEASE CHANGE THE TITLE OF THREAD TO "PHP Trouble displaying array"?

---

### Post by ibuclaw on 2010-09-24
> **k33bz said:**
> MODS, CAN YOU PLEASE CHANGE THE TITLE OF THREAD TO "PHP Trouble displaying array"?
Done!

We have a report button for that sort of request (even though the image for it says - rather confusingly - 'report abuse').

---

### Post by k33bz on 2010-09-24
> **ibuclaw said:**
> Done!

We have a report button for that sort of request (even though the image for it says - rather confusingly - 'report abuse').

oh, I thought that just meant to report the post as something that needs to be looked at for closure. Thanks

A LITTLE UPDATE, I AM STILL WORKING ON GETTING THAT FILE CUT DOWN, IT WILL BE AWHILE BEFORE I POST IT.

---

### Post by k33bz on 2010-09-24
I just noticed something on line 1186
```
if (/*$values["values"][$field["name"]] && */file_exists($file_name)) {
```

however the "/*$values["values"][$field["name"]] && */" is greyed out (like it is a comment) instead of the colorful reds and greens.

Could this be my problem, if so how do I fix this?

---

### Post by k33bz on 2010-09-24
Since no one replied to previous post I am going to guess that it should be like that.

Anyway I have took out ALL comments, except a few that I am not sure if should be there or not, more like different variables you could choose.
Took out alot of double spaces, and tried to go through and remove the stuff that is not applied to the problem at hand. Still over a 1000 lines of code. So I wont post that. However I am going to post these two snippets, since it seems to be directly involved. And if there is a fix I can try to apply to all of the ones similar to it.

/lib/forms.php line 5
```

$form_months = array (1 => "January" , "February" , "March" , "April" , "May" , "June" , "July" , "August" , "September" , "October" , "November" , "December");


```



/lib/forms.php lines 1108 - 1131
```

case "month":

								if (($field["fields"]["month"]["empty"] == "true"))  {

									$months[0] = "--" ;

								}



								global $form_months;



								if (is_array($months))

									$formmonths = array_merge($months, $form_months);

								else

									$formmonths = $form_months;



								$current_field .= $html->FormSelect(

																		$field["name"]."_month" , 

																		$formmonths, 

																		$this->templates , 

																		"DateSelect", 

																		$month_selected,

																		array() , 

																		array("DISABLED" => ($field["fields"]["month"]["editable"] == "false") ? "DISABLED" : "")

																	);



								$current_field .= $val["separator"];

							break;

```

Now as far as numbers, like those for the dates and years, I cant seem to find a list defined like it was defined for months on line 5. Can those numbers be automated some how, if so how would that code look?

by the way, there is what appears to be a very big empty space, need to scroll all the way over to see it.

---

### Post by k33bz on 2010-09-24
Ok, I believe I grabbed the whole source where it is talking about dates. Some reason even talks about time, which I dont have available anyway on the site.
 Still look above to see where it is defined on line 5
```

case "date":



				if (is_array($field["fields"])) {



					echo "<pre style=\"background-color:white\">";

					print_r($field);

					print_r($values["values"]);



					$html = new CHtml;



					//do some variables cleaning

					if (is_array($years))

						unset($years);

					if (is_array($days))

						unset($days);

					if (is_array($months))

						unset($months);



					



					$date_vals = &$values["values"][$field["name"]];



					if ($date_vals > 1000) {



						//setting the previous values

						$year_selected = isset($values["values"][$field["name"] ."_year"]) ? $values["values"][$field["name"] ."_year"] : @date("Y" , $date_vals );

						$month_selected = isset($values["values"][$field["name"] ."_month"]) ? $values["values"][$field["name"] ."_month"] : @date("n" , $date_vals );

						$day_selected = isset($values["values"][$field["name"] ."_day"]) ? $values["values"][$field["name"] ."_day"] : @date("j" , $date_vals );



						//crap, adding the time values too

						$hour_selected = isset($values["values"][$field["name"] ."_hour"]) ? $values["values"][$field["name"] ."_hour"] : @date("G" , $date_vals );

						$minute_selected = isset($values["values"][$field["name"] ."_minute"]) ? $values["values"][$field["name"] ."_minute"] : @date("i" , $date_vals );

						$second_selected = isset($values["values"][$field["name"] ."_second"]) ? $values["values"][$field["name"] ."_second"] : @date("s" , $date_vals );

						

					} else {



						$fld = $field["fields"];



						//setting the default value 						

						$year_selected = $fld["year"]["default"] == "now" ? date("Y") : $fld["year"]["default"];

						$month_selected = $fld["month"]["default"] == "now" ? date("n") : $fld["month"]["default"];

						$day_selected = $fld["day"]["default"] == "now" ? date("j") : $fld["day"]["default"];



						//crap, adding the time values too

						$hour_selected = $fld["hour"]["default"] == "now" ? date("G") : $fld["hour"]["default"];

						$minute_selected = $fld["minute"]["default"] == "now" ? date("i") : $fld["minute"]["default"];

						$second_selected = $fld["second"]["default"] == "now" ? date("s") : $fld["second"]["default"];						

					}



					foreach ($field["fields"] as $key => $val) {

						switch ($key) {

							case "year":

								if ($field["fields"]["year"]["empty"] == "true") {

									$years[0] = "--" ;

								}

								

								for ($i = $field["fields"]["year"]["from"] ; $i <= $field["fields"]["year"]["to"] ; $i++ )

									$years[$i] = $i;									



								$current_field .= $html->FormSelect(

																		$field["name"]."_year" , 

																		$years , 

																		$this->templates , 

																		"DateSelect", 

																		$year_selected , 

																		array() , 

																		array("DISABLED" => ($field["fields"]["year"]["editable"] == "false") ? "DISABLED" : "")									

																	);



								$current_field .= $val["separator"];

							break;



							case "day":

								if ($field["fields"]["day"]["empty"] == "true") {

									$days[0] = "--" ;

								}



								for ($i = 1 ; $i <= 31 ; $i++ )

									$days[$i] = sprintf("%02d",$i);



								$current_field .= $html->FormSelect(

																		$field["name"]."_day" , 

																		$days , 

																		$this->templates , 

																		"DateSelect", 

																		$day_selected,

																		array() , 

																		array("DISABLED" => ($field["fields"]["day"]["editable"] == "false") ? "DISABLED" : "")

																	);

								$current_field .= $val["separator"];

							break;



							case "month":

								if (($field["fields"]["month"]["empty"] == "true"))  {

									$months[0] = "--" ;

								}



								//importing the months from global

								global $form_months;



								if (is_array($months))

									$formmonths = array_merge($months, $form_months);

								else

									$formmonths = $form_months;



								//ehcking if the dates must apear like strings or numbers

								$current_field .= $html->FormSelect(

																		$field["name"]."_month" , 

																		$formmonths, 

																		$this->templates , 

																		"DateSelect", 

																		$month_selected,

																		array() , 

																		array("DISABLED" => ($field["fields"]["month"]["editable"] == "false") ? "DISABLED" : "")

																	);



								$current_field .= $val["separator"];

							break;



							case "hour":

								for ($i = 0; $i <= 23; $i++ )

									$hours[$i] = sprintf("%02d",$i);;									



								$current_field .= $html->FormSelect(

																		$field["name"]."_hour" , 

																		$hours , 

																		$this->templates , 

																		"DateSelect", 

																		$hour_selected , 

																		array() , 

																		array("DISABLED" => ($field["fields"]["hour"]["editable"] == "false") ? "DISABLED" : "")									

																	);



								$current_field .= $val["separator"];

							break;



							case "minute":

								for ($i = 0; $i <= 59; $i++ )

									$minutes[$i] = sprintf("%02d",$i);;									



								$current_field .= $html->FormSelect(

																		$field["name"]."_minute" , 

																		$minutes , 

																		$this->templates , 

																		"DateSelect", 

																		$minute_selected , 

																		array() , 

																		array("DISABLED" => ($field["fields"]["minute"]["editable"] == "false") ? "DISABLED" : "")									

																	);



								$current_field .= $val["separator"];

							break;



							case "second":

								for ($i = 0; $i <= 59; $i++ )

									$seconds[$i] = sprintf("%02d",$i);;									



								$current_field .= $html->FormSelect(

																		$field["name"]."_second" , 

																		$seconds , 

																		$this->templates , 

																		"DateSelect", 

																		$second_selected , 

																		array() , 

																		array("DISABLED" => ($field["fields"]["minute"]["editable"] == "false") ? "DISABLED" : "")									

																	);



								$current_field .= $val["separator"];

							break;



						}						

					}					

				}				



				//if the field hs description then i add the valign code

				$current_field_extra = $field["description"] ? $this->templates->blocks["TopAlign"]->output : ""; 



			break;
```

oh, almost forgot, I took out the indexing from line 5, so instead of it starting out like
$form_months = array (1 => "January"
it is now starting out like
$form_months = array ( "January"

---

### Post by k33bz on 2010-10-01
Ok, not much to update. However I am more than sure what the problem is. This code was written for a version of PHP4 (I am more than sure on this). However I am running the latest PHP5.

Where can I go that will tell me how to update the code so it will work on PHP5. Not sure how to, or what keywords to search for, to find my answer on this one. I have only came up with one hit [http://www.webmaster-talk.com/php-forum/78717-differences-between-php4-and-php5.html]("http://www.webmaster-talk.com/php-forum/78717-differences-between-php4-and-php5.html") but I need more references.

Thanks

---

### Post by Maheriano on 2010-10-03
Anything written for PHP4 will work in PHP5, that's likely not your problem. 

If you want you can send me all the files you're using or your FTP login and I'll take a few minutes to fix it. Otherwise go to phpfreaks.com and post your problem there. But beware, they won't even look at more than 50 lines of code.

---

### Post by k33bz on 2010-10-06
> **Maheriano said:**
> Anything written for PHP4 will work in PHP5, that's likely not your problem. 

If you want you can send me all the files you're using or your FTP login and I'll take a few minutes to fix it. Otherwise go to phpfreaks.com and post your problem there. But beware, they won't even look at more than 50 lines of code.

Sent you a message :) And ya I know they wont, I have tried that, as well as a few other php forum sites :)

---

### Post by SeijiSensei on 2010-10-06
> **k33bz said:**
> lib/forms.php line 5
```

$form_months = array (1 => "January" , "February" , "March" , "April" , "May" , "June" , "July" , "August" , "September" , "October" , "November" , "December");

```

Entries of the form "x"=>"y" indicate associative arrays.  If you just want a numbered list then remove the '1=>' and include only the months.  Be aware, though, that PHP numbers from zero like most everything else in the Unix world.  So $form_months[0] will equal January, and $form_months[12] will be undefined.

If the first entry is "", then $form_months[0] will return an empty string, and $form_months[1] will return "January".  One convenient trick this permits is to assign the first entry a value like "Select a Month" which will appear by default in the drop-down box.

Usually I create drop-down boxes from a simple function I wrote.  It requires an associative array of "key"=>"value" pairs that are used to populate the select control.  The function looks like this:

```

function make_select($name,$options,$selected[,$extra=""]) {

    # make a select box
    # $name = name of the HTML field
    # $options = associative array of key/value pairs to populate select box
    # $selected = a previously selected value or "" if none
    # $extra = optional additional text for styles, etc.

    $output="";
    $output.="\n<select name=\"$name\" $extra >\n";

    while (list($key,$val) = each($options)) {
         $output.="<option value=\"$key\"";
         if ($key==$selected) {
            $output.=" selected";
         }
         $output.=">".trim($val)."</option>\n";
     }
     $output.="</select>\n";

     return $output;

}
```

I wrote this some years ago; today I'd use a "foreach ($options as $key=>$val)" construct instead of a while() loop.

---

### Post by gully_mi_seh on 2011-02-27
You should try to upgrade your version of php to 5+ and modify your class contents 
php4 often use var [-X for variable's declaration but you should be using :idea: private, public. Php 4 is kind of based on pseudo-objets so if you want to use php oriented objet to the fullest start by using a version later than 5.:o

---

