# Oracle SQL Toy Library Database

A relational database project supporting the operations of a toy library across two branches: Fremantle and White Gum Valley.

The project covers database modelling, normalisation, Oracle implementation and SQL reporting. It manages toy inventory and storage alongside memberships, borrowing, volunteer shifts, repairs and events.

Developed by Vaibhav Saini for ICT285 at Murdoch University.
[View or download my SQL database assignment](PASTE_FILE_URL_HERE)

## Project Objectives

- Organise operational information into a consistent relational database.
- Track individual toys, their assigned storage locations and borrowing history.
- Record member donations, volunteer participation and completed repairs.
- Support event registration and attendance reporting.
- Use constraints and database controls to protect data integrity.
- Create reusable SQL views for operational queries.

## Database Design

The schema contains 12 related tables.

| Table | Purpose |
|---|---|
| MEMBER | Member details |
| CATEGORY | Toy classifications |
| BRANCH | Library branches |
| ROOM | Rooms identified within each branch |
| LOCATION | Shelf or room-only storage locations |
| TOY | Individual toys, condition, acquisition and lending status |
| LOAN | Borrowing transactions, due dates and returns |
| SHIFT | Dated volunteer shifts at each branch |
| SHIFT_SIGNUP | Members registered for shifts |
| REPAIR | Completed repairs and the members responsible |
| EVENT | Event details and registration capacity |
| EVENT_ATTENDANCE | Member registrations and attendance |

### Modelling Decisions

- Used a composite room key so different branches can reuse room numbers.
- Represented member shift signups and event registrations through linking tables.
- Separated repair records to retain repeated repairs to the same toy.
- Supported room-only storage through an optional shelf number.
- Distinguished a toy's fitness for lending from its current loan availability.
- Calculated borrowing allowances from contribution records rather than storing a value that could become outdated.

The report includes an entity relationship diagram created in Microsoft Visio, a relational schema in Third Normal Form and a detailed data dictionary.

## SQL Skills Demonstrated

- Relational modelling and normalisation to 3NF.
- Oracle data types and table definitions.
- Primary keys, composite keys and foreign keys.
- NOT NULL, UNIQUE and CHECK constraints.
- Sample data insertion.
- CREATE OR REPLACE VIEW statements.
- INNER JOIN and LEFT JOIN operations.
- GROUP BY and COUNT for summary reporting.
- NOT EXISTS for identifying missing related records.
- UNION for combining query results.
- Date filtering using SYSDATE, TRUNC and ADD_MONTHS.
- Access permissions using GRANT statements.

## Data Integrity and Business Rules

The implementation described in the report includes controls for:

- Valid relationships between members, toys, loans and other records.
- Preventing multiple unreturned loans for the same toy.
- Preventing loans of toys marked unfit for lending.
- Restricting loan dates and return dates.
- Maintaining consistent battery and donor information.
- Preventing duplicate shift signups and event registrations.
- Protecting event capacity, including capacity reductions.
- Retaining historical records through restricted parent deletion.

The report distinguishes rules enforced by database constraints, indexes and triggers from enterprise rules requiring additional transaction checks.

## Operational Reporting Views

Ten SQL views address practical reporting requirements.

| View | Reporting purpose |
|---|---|
| ViewA | Toy catalogue with category and storage information |
| ViewB | Toys at a specified branch, room and shelf |
| ViewC | Borrowing counts by toy category |
| ViewD | Next month's shifts without volunteers |
| ViewE | Current month's shifts and volunteer assignments |
| ViewF | Outstanding overdue loans and days late |
| ViewG | Members contributing through shifts or repairs this month |
| ViewH | Borrowing history for a specified member |
| ViewI | Registrations for a specified event and date |
| ViewJ | Repairs completed by a specified member |

These views demonstrate how related operational records can be combined into information useful for inventory management, scheduling and follow-up.

## Tools

- Oracle Database
- Oracle SQL*Plus
- Microsoft Visio
- Microsoft Word

## Reviewing the Project

Open the uploaded assignment report to review:

1. The revised entity relationship diagram and design assumptions.
2. The relational schema and explanation of Third Normal Form.
3. Column definitions, data types and constraints.
4. Referential integrity and business rules.
5. The implementation summary.
6. SQL definitions for all ten views.
7. Screenshots of query outputs.

The report documents the database implementation and includes the view SQL. Separate database setup scripts are needed to recreate the complete database.

## Reporting Considerations

Several views use the current system date to select the current or following month. Their results depend on the execution date and available sample records.

Other views deliberately filter specific members, storage locations or events to answer the assignment's reporting requirements.

## Practical Relevance

This project demonstrates how to structure operational data, preserve relationships and produce reusable reports.

Although the scenario is a toy library, the underlying skills apply to inventory tracking, asset maintenance, staff scheduling and other systems that depend on reliable relational data.
