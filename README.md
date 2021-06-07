# Design Patterns in Java: Our Stock Exchange System

## Objective

  - Didactically exemplify the implementation of the main object-oriented design patterns in native Java.

## Approach

  - All design patterns are implemented through use cases for a stock exchange didactic system.
  - Each design pattern has:
    - The implementation based on a use case that is specified in the use case specification section.
    - A package located in the *com.phcarvalhome.pattern* package which has:
      - A *<PATTERN_NAME>Test* class with test methods.
      - A *core* package with the main implementation of the design pattern.
      - A *business* package with the complementary implementations needed to meet the use case.

## Use Case Specifications

### 1. UC01 - Create Department Notification

  - [x] **Design pattern:** Abstract Factory Pattern
  - **Prerequisite:** N/A

#### 1.1. Business rules

    1.1.1. A notification must consist of:
      - Destiny
      - Type of notification
      - Creation date and time
    1.1.2. Only Open Market and Stopped Market notifications should be considered.
    1.1.3. New notifications can be considered later.
    1.1.4. Only IT and HR departments should be considered.
    1.1.5. New departments can be considered later.

#### 1.2. Implementation Details

  - [x] **Package:** *com.phcarvalhome.pattern.abstractfactory*
  - About business rules
    - Each method of the *INotificationFactory* interface represents a notification.
    - Each implementation of the *INotificationFactory* interface represents a department.
  - About the design pattern
    - Each implementation of the *INotificationFactory* interface represents a "Factory".
    - The *Operation* and *Stock* classes represent the "Factory".
  
---

### 2. UC02 - Create batch notifications

  - [x] **Design pattern:** Singleton Pattern
  - **Prerequisite:** UC01

#### 2.1. Business rules

    2.1.1. Only the batch of department notifications should be considered.
    2.1.2. New batches can be considered later.
    2.1.3. Only IT and HR departments should be part of the department notification batch.

#### 2.2. Implementation Details

  - [x] **Package:** *com.phcarvalhome.pattern.singleton*
  - About business rules
    - The *DepartmentNotificationFactoryBatch* class represents the department notification batch.
  - About the design pattern
    - The *DepartmentNotificationFactoryBatch* class represents the "Singleton".
  
---

### 3. UC03 - Duplicate market operation

  - [x] **Design pattern:** Prototype Pattern
  - **Prerequisite:** N/A
  
  #### 3.1. Business rules

    3.1.1. A market operation carried out previously can be duplicated.
    3.1.2. A market operation must consist of:
      - Operation type
      - Action
      - Number of shares
    3.1.3. A stock must consist of the type of stock and the price.
    3.1.4. The duplicated market operation must be composed of the same values ​​as the original market operation, with
    exception of the value of the share price that must be recalculated.

  #### 3.2. Implementation Details

  - [x] **Package:** *com.phcarvalhome.pattern.prototype*
  - About the design pattern
    - Each implementation of the *IPrototype<T>* interface represents a "Prototype".
    - The *Operation* and *Stock* classes represent the "Prototypes".

---

### 4. UC04 - Create market operation schedule

  - [x] **Design pattern:** Builder Pattern
  - **Prerequisite:** UC03
  
  #### 4.1. Business rules

    4.1.1. A market operation can be scheduled.
    4.1.2. An appointment must consist of:
      - Market operation
      - Start date
      - End date
      - Scheduled time
      - Type of recurrence: No recurrence, Daily, Weekly and Monthly
      - Status: Active and Inactive
      - Email list for notification

  #### 4.2. Implementation Details

  - [x] **Package:** *com.phcarvalhome.pattern.builder*
  - About the design pattern
    - The *OperationScheduleBuilder* class represents the "Builder".

--- 

### 5. UC05 - Consume External System Notification

  - [x] **Design pattern:** Object Pool Pattern
  - **Prerequisite:** UC01
  
  #### 5.1. Business rules

    5.1.1. A market operation can be scheduled.
    5.1.2. An appointment must consist of:
      - Market operation
      - Start date
      - End date
      - Scheduled time
      - Type of recurrence: No recurrence, Daily, Weekly and Monthly
      - Status: Active and Inactive
      - Email list for notification

  #### 5.2. Implementation Details

  - [x] **Package:** *com.phcarvalhome.pattern.objectpool*
  - About the design pattern
    - The *OperationScheduleBuilder* class represents the "Builder".

---

### 6. UC06 - Define User

  - [x] **Design pattern:** Private Data Class Pattern
  - **Prerequisite:** UC03
  
  #### 6.1. Business rules

    6.1.1. A user must consist of:
      - Identifier
      - Email
      - Password
      - Bank branch
      - Bank account
      - List of market operations
    6.1.2. Password can only be obtained in encrypted form.
    6.1.3. Password can only be set with current password validation
    6.1.4. Branch and bank account can only be set up with current password validation
    6.1.5. The list of market operations can only be obtained immutably
    6.1.6. The list of market operations can only be configured by adding a new market operation.

  #### 6.2. Implementation Details

  - [x] **Package:** *com.phcarvalhome.pattern.privatedataclass*
  - About the design pattern
    - The *User* class represents the "Private Data Class".
    
---

### 7. UC07 - Get, Save, Update, and Remove User

  - [x] **Design pattern:** Adapter Pattern
  - **Prerequisite:** UC06
  
  #### 7.1. Business rules

    7.1.1. A user can be obtained, saved, updated and removed.

  #### 7.2. Implementation Details

  - [x] **Package:** *com.phcarvalhome.pattern.adapter*
  - About the design pattern
    - The *EntityDAO* class represents the old repository access API.
    - The *IEntityDAO<T>* interface represents the new repository access API.
    - The *UserDAOObjectAdapter* class represents an "Object Adapter" that adapts the old API to the new API.
    - The *UserDAOClassAdapter* class represents a "Class Adapter" that adapts the old API to the new API.

---

### 8. UC08 - Generate User Market Transaction Report

  - [x] **Design pattern:** Bridge Pattern
  - **Prerequisite:** UC03
  
  #### 8.1. Business rules

    8.1.1. A report of a user's market operations can be generated.

  #### 8.2. Implementation Details

  - [x] **Package:** *com.phcarvalhome.pattern.bridge*
  - About the design pattern
    - The *EntityDAO* class represents the old repository access API.
    - The *IEntityDAO<T>* interface represents the new repository access API.
    - The *UserDAOObjectAdapter* class represents an "Object Adapter" that adapts the old API to the new API.
    - The *UserDAOClassAdapter* class represents a "Class Adapter" that adapts the old API to the new API.
  
  ---

### 9. UC09 - Generate market trade scheduling events

  - [x] **Design pattern:** Composite Pattern
  - **Prerequisite:** UC04
  
  #### 9.1. Business rules

    9.1.1. Events from a market trade schedule can be generated.

  #### 9.2. Implementation Details

  - [x] **Package:** *com.phcarvalhome.pattern.composite*
  - About the design pattern
    - The *EntityDAO* class represents the old repository access API.
    - The *IEntityDAO<T>* interface represents the new repository access API.
    - The *UserDAOObjectAdapter* class represents an "Object Adapter" that adapts the old API to the new API.
    - The *UserDAOClassAdapter* class represents a "Class Adapter" that adapts the old API to the new API.
