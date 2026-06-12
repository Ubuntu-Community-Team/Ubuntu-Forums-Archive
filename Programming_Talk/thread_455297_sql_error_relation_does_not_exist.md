---
title: "sql error: relation does not exist"
date: 2007-05-26
forum: Programming Talk
---

### Post by Hansmc on 2007-05-26
I am working with a sql database in pgAdmin 3 and postgres 8.2.

I made several databases and they worked fine. Then I made a new one and removed all the others, but it does not work right.

I can make or change tables fine. I can add and see the data by right-clicking and choosing 'view data'. But when I try to access the data in the table with sql I get this error:

ERROR:  relation "town" does not exist

town is the name of my table.

The same error comes for all the tables I tried. I made some little simple tables and they get the same error. I tried lots of different versions of adding and viewing data from these tables, but they all get the same error. The same error message comes through psgl. This thing is not foolproof. :)

What did I do wrong? Can it be fixed?





The two main tables that I am trying to populate are:
-- Table: "Town"

-- DROP TABLE "Town";

CREATE TABLE "Town"
(
  "Name" varchar(30) NOT NULL, -- The name of the town.
  "State" varchar(2) NOT NULL, -- The state of the town. Uses the two letter postal abbreviation.
  "Zipcode" varchar(5), -- The zip code of the town
  "Location" point, -- The latitude and longitude of the town
  "Altitude" int4, -- The altitude of the town
  "Key" int4 NOT NULL DEFAULT nextval('"Town_Key_seq"'::regclass), -- A key for linking with weather table
  CONSTRAINT "key" PRIMARY KEY ("Key"),
  CONSTRAINT "Town_must_be_unique_for_state" UNIQUE ("Name", "State")
) 
WITHOUT OIDS;
ALTER TABLE "Town" OWNER TO postgres;
COMMENT ON COLUMN "Town"."Name" IS 'The name of the town.';
COMMENT ON COLUMN "Town"."State" IS 'The state of the town. Uses the two letter postal abbreviation.';
COMMENT ON COLUMN "Town"."Zipcode" IS 'The zip code of the town';
COMMENT ON COLUMN "Town"."Location" IS 'The latitude and longitude of the town';
COMMENT ON COLUMN "Town"."Altitude" IS 'The altitude of the town';
COMMENT ON COLUMN "Town"."Key" IS 'A key for linking with weather table';


NOTE the db is also named weather.
-- Table: "Weather"

-- DROP TABLE "Weather";

CREATE TABLE "Weather"
(
  "Key" int4 NOT NULL, -- The foreign key
  "Date" date NOT NULL, -- Date that the weather was recorded
  "Hi_Temp" float4, -- The high temp for the day
  "Lo_Temp" float4, -- The low temp for the day
  "Snow" float4 DEFAULT 0, -- The snow fall for the day
  "Rain" float4, -- The rain for the day
  CONSTRAINT "Only_one_date_per_town" PRIMARY KEY ("Key", "Date"),
  CONSTRAINT "Town_not_available" FOREIGN KEY ("Key")
      REFERENCES "Town" ("Key") MATCH SIMPLE
      ON UPDATE CASCADE ON DELETE CASCADE
) 
WITHOUT OIDS;
ALTER TABLE "Weather" OWNER TO postgres;
COMMENT ON COLUMN "Weather"."Key" IS 'The foreign key';
COMMENT ON COLUMN "Weather"."Date" IS 'Date that the weather was recorded';
COMMENT ON COLUMN "Weather"."Hi_Temp" IS 'The high temp for the day';
COMMENT ON COLUMN "Weather"."Lo_Temp" IS 'The low temp for the day';
COMMENT ON COLUMN "Weather"."Snow" IS 'The snow fall for the day';
COMMENT ON COLUMN "Weather"."Rain" IS 'The rain for the day';

---

### Post by tturrisi on 2007-05-26
table names are case sensitive.

---

### Post by Hansmc on 2007-05-26
Still did not work. But it put me on to something that did . . . 

INSERT INTO "Town" ("Name", "State", "Zipcode")
VALUES ('Some Town', 'ST', '12345');

Double quote all names!

Thanks for your reply.

Have a good day.

---

