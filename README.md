# RAP100 Tutorial Backend
This repository contains the backend implementation of the **SAP RAP100 Tutorial**, demonstrating the **ABAP RESTful Application Programming Model (RAP)**.  
It covers all major RAP layers: persistence, behavior definition & projection, CDS views, and annotations for UI exposure.

## 📂 Repository Structure
- **Database Table**
  - `ZRAP100_ATRAV090`  
    Defines the persistence layer for travel data.  
    Includes fields such as `TravelID`, `AgencyID`, `CustomerID`, `BeginDate`, `EndDate`, `BookingFee`, `TotalPrice`, and audit fields (`CreatedBy`, `LastChangedAt`).

  ![Database Table](DB%20Table.png)

- **Behavior Definition**
  - `ZRAP100_R_TRAVELTP_090`  
    Contains the RAP behavior definition for the Travel entity.  
    Defines operations like `create`, `update`, `delete`, and custom actions:  
    - `acceptTravel`  
    - `rejectTravel`  
    - `deductDiscount`  
    - `copyTravel`  

    Also includes draft actions: `Activate`, `Discard`, `Edit`, `Resume`, `Prepare`.

  ![Behavior Definition](Behavior%20definition.png)

- **Behavior Projection**
  - `ZRAP100_C_TRAVELTP_090`  
    Projects the behavior to the consumer view.  
    Exposes standard and custom actions to the UI/service layer.

  ![Behavior Projection](Behavior%20projection.png)

- **Interface View**
  - `ZRAP100_R_TRAVELTP_090`  
    Core data service entity view with associations to related entities (`Agency`, `Customer`, `OverallStatus`, `Currency`).  
    Includes semantics, consumption hints, and annotations for file attachments.

  ![Interface View](Interface%20view.png)

- **Projection View**
  - `ZRAP100_C_TRAVELTP_090`  
    Provides the consumer-facing projection of the Travel entity.  
    Supports search, associations, and query contracts for OData exposure.

  ![Projection View](Projection%20view.png)

- **Metadata Extension**
  - `ZRAP100_C_TRAVELTP_090`  
    UI annotations defining how Travel data should be displayed in the Fiori Elements app.  
    Configures `lineItem`, `identification`, and action buttons (e.g., **Copy Travel**, **Accept Travel**, **Reject Travel**, **Deduct Discount**).

  ![Metadata Extension](Metdata%20extension.png)

## 🚀 Features Implemented
- Full RAP stack implementation
- Draft-enabled actions and validations
- Custom business actions (`deductDiscount`, `copyTravel`, etc.)
- UI annotations for Fiori Elements
- Associations to standard demo entities (`/DMO/I_Agency`, `/DMO/I_Customer`, etc.)
- Attachment handling with MIME type validation

## 📘 Prerequisites
- SAP BTP ABAP Environment or SAP S/4HANA system with RAP support
- ABAP Development Tools (ADT) in Eclipse
- Access to `/DMO/*` demo content for associations

## ▶️ How to Run
1. Import the repository into your ABAP system.
2. Activate all CDS, behavior, and table artifacts.
3. Use **Fiori Elements Preview** (from ADT) to test the Travel entity app.
4. Try actions like *Create Travel*, *Accept Travel*, *Reject Travel*, and *Deduct Discount*.



