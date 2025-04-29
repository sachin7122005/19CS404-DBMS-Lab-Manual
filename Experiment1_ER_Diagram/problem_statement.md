# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - RAGUL T R

## Scenario Chosen:
University 

## ER Diagram:

![Screenshot 2025-04-29 122653](https://github.com/user-attachments/assets/e02390e0-823d-4602-bb5e-c079f563cfee)


## Entities and Attributes:
STUDENT
Attributes: REG (PK), NAME, DOB, DEPT

COURSE
Attributes: COURSEID (PK), NAME, CREDITS

PROGRAM
Attributes: PROGRAM ID (PK), NAME, CREDIT/POINTS, BRANCHES

COLLEGE
Attributes: CID (PK), NAME, DEGREE

FACULTY
Attributes: FID (PK), NAME, BRANCH, EXPERIENCE

UNIVERSITY (UNI)
Attributes: Not explicitly shown, assumed to have a unique identifier like UID


...

## Relationships and Constraints:
- ATTEMPTS (Between STUDENT and COURSE)

GRADE

SEM

CREDITS

ENROLL (Between STUDENT and PROGRAM)

No attributes

CONTAINS (Between PROGRAM and COURSE)

No attributes

HAS (Between COLLEGE and FACULTY)

No attributes

HAS (Between COLLEGE and UNI)

No attributes

HAS (Between UNI and FACULTY)

No attributes
...

## Extension (Prerequisite / Billing):
ATTEMPTS (STUDENT–COURSE)
Attributes: SEM, GRADE, CREDITS

Cardinality: M:N (Many students can attempt many courses)

ENROLL (STUDENT–PROGRAM)
Attributes: None

Cardinality: M:N (Many students can enroll in many programs)

CONTAINS (PROGRAM–COURSE)
Attributes: None

Cardinality: 1:N (One program contains many courses)

HAS (COLLEGE–FACULTY)
Attributes: None

Cardinality: 1:N (A college can have many faculty members)

HAS (COLLEGE–UNIVERSITY)
Attributes: None

Cardinality: M:1 (Many colleges belong to one university)

HAS (UNIVERSITY–FACULTY)
Attributes: None

Cardinality: N:M (Faculty may be associated with multiple universities — though this is rare, so might be 1:N in some implementations)



## Design Choices:
Surrogate Keys like REG, COURSEID, PROGRAM ID, CID, and FID are used as unique identifiers.

Multi-valued Relationships (like M:N in ATTEMPTS, ENROLL) are converted into associative entities with attributes.

Normalization: Data appears normalized to reduce redundancy (e.g., separating PROGRAM and COURSE).

Hierarchical Structure: UNIVERSITY → COLLEGE → FACULTY shows a top-down hierarchy.

Attribute Placement: Attributes are placed meaningfully — e.g., SEM and GRADE are properties of ATTEMPTS, not of STUDENT or COURSE alone.
## RESULT
Tables:
STUDENT (REG, NAME, DOB, DEPT)

COURSE (COURSEID, NAME, CREDITS)

PROGRAM (PROGRAM ID, NAME, CREDIT_POINTS, BRANCHES)

COLLEGE (CID, NAME, DEGREE)

FACULTY (FID, NAME, BRANCH, EXPERIENCE)

UNIVERSITY (UID, NAME) (Assumed attributes)

Associative (Relation) Tables:
ATTEMPTS (REG, COURSEID, SEM, GRADE, CREDITS)

ENROLL (REG, PROGRAM ID)

CONTAINS (PROGRAM ID, COURSEID)

COLLEGE_UNI (CID, UID)

COLLEGE_FACULTY (CID, FID)

UNI_FACULTY (UID, FID) (if applicable)
