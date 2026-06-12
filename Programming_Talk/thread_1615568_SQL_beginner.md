---
title: "SQL beginner"
date: 2010-11-07
forum: Programming Talk
---

### Post by cap10Ibraim on 2010-11-07
I generated the following SQL script using mySQL workbench 
```

SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0;
SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0;
SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='TRADITIONAL';

CREATE SCHEMA IF NOT EXISTS `mydb` DEFAULT CHARACTER SET latin1 COLLATE latin1_swedish_ci ;
USE `mydb` ;

-- -----------------------------------------------------
-- Table `mydb`.`Customer`
-- -----------------------------------------------------
CREATE  TABLE IF NOT EXISTS `mydb`.`Customer` (
  `idCustomer` INT NOT NULL ,
  `name` VARCHAR(45) NULL ,
  PRIMARY KEY (`idCustomer`) )
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Cachier`
-- -----------------------------------------------------
CREATE  TABLE IF NOT EXISTS `mydb`.`Cachier` (
  `idCachier` INT NOT NULL ,
  PRIMARY KEY (`idCachier`) )
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Order`
-- -----------------------------------------------------
CREATE  TABLE IF NOT EXISTS `mydb`.`Order` (
  `idOrder` INT NOT NULL ,
  `order_date` DATETIME NULL ,
  `Customer_idCustomer` INT NOT NULL ,
  `Cachier_idCachier` INT NOT NULL ,
  PRIMARY KEY (`idOrder`) ,
  INDEX `fk_Order_Customer1` (`Customer_idCustomer` ASC) ,
  INDEX `fk_Order_Cachier1` (`Cachier_idCachier` ASC) ,
  CONSTRAINT `fk_Order_Customer1`
    FOREIGN KEY (`Customer_idCustomer` )
    REFERENCES `mydb`.`Customer` (`idCustomer` )
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_Order_Cachier1`
    FOREIGN KEY (`Cachier_idCachier` )
    REFERENCES `mydb`.`Cachier` (`idCachier` )
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Product`
-- -----------------------------------------------------
CREATE  TABLE IF NOT EXISTS `mydb`.`Product` (
  `idProduct` INT NOT NULL ,
  `product_name` VARCHAR(45) NULL ,
  `exp_date` DATE NULL ,
  `quantity` VARCHAR(45) NULL ,
  `price` INT NULL ,
  PRIMARY KEY (`idProduct`) )
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Employee`
-- -----------------------------------------------------
CREATE  TABLE IF NOT EXISTS `mydb`.`Employee` (
  `idEmployee` INT NOT NULL ,
  `employee_name` VARCHAR(45) NULL ,
  `Employee_idEmployee` INT NOT NULL ,
  PRIMARY KEY (`idEmployee`) ,
  INDEX `fk_Employee_Employee1` (`Employee_idEmployee` ASC) ,
  CONSTRAINT `fk_Employee_Employee1`
    FOREIGN KEY (`Employee_idEmployee` )
    REFERENCES `mydb`.`Employee` (`idEmployee` )
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Cachier_has_Employee`
-- -----------------------------------------------------
CREATE  TABLE IF NOT EXISTS `mydb`.`Cachier_has_Employee` (
  `Cachier_idCachier` INT NOT NULL ,
  `Employee_idEmployee` INT NOT NULL ,
  `work_time` VARCHAR(45) NOT NULL ,
  PRIMARY KEY (`work_time`) )
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `mydb`.`Order_has_Product`
-- -----------------------------------------------------
CREATE  TABLE IF NOT EXISTS `mydb`.`Order_has_Product` (
  `Order_idOrder` INT NOT NULL ,
  `Product_idProduct` INT NOT NULL ,
  `order_quantity` VARCHAR(45) NULL ,
  PRIMARY KEY (`Order_idOrder`, `Product_idProduct`) )
ENGINE = InnoDB;



SET SQL_MODE=@OLD_SQL_MODE;
SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS;
SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS;

```
is this standard syntax , if not how can I configure workbench to work as standard as possible ? !

---

### Post by ja660k on 2010-11-07
Thats about as "standard" as you can get workbench.

usually we dont need all the `quotes`
And there are some handy shortcuts 
ie
```

CREATE  TABLE IF NOT EXISTS `mydb`.`Customer` (
  `idCustomer` INT NOT NULL ,
  `name` VARCHAR(45) NULL ,
  PRIMARY KEY (`idCustomer`) )
ENGINE = InnoDB;

```
```

use mydb;
CREATE  TABLE IF NOT EXISTS customer (
  idcustomer INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(45) NULL
);

```

You should let the db manage the primary keys by using AUTO_INCREMENT
And the default storage engine for mysql is InnoDB so we dont need to specify ENGINE=InnoDB

this is just how i would write my sql statements/queries

---

### Post by cap10Ibraim on 2010-11-07
thanks , before Ubuntu and MySQL I used Sybase Power Designer in Windows , there are some major differences when designing the model 
[COLOR="Red"]*i  can't find the association link*[/COLOR] (between two entities) in the draw panel , so I'm always using relationships is it an option for the model [COLOR="red"]*or not available in workbench designer ?!*[/COLOR]

---

