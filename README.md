# django-camms
The Campus Asset & Maintenance Management System (CAMMS) is a Django-based web application developed to manage university campus infrastructure and maintenance activities.

The system maintains structured data for buildings, rooms, assets, and maintenance requests while enforcing proper validations and relationships using Django ORM. No raw SQL is used in this project.

🛠️ Tech Stack

Python

Django

SQLite (default database)

Django Admin Panel

🏗️ Project Structure

The project strictly contains two Django apps:

1️⃣ assets

Handles infrastructure and asset management.

Models:

Building – Stores building details (unique name and block code).

Room – Linked to a building with floor validation.

Asset – Linked to a room with purchase date validation and operational status.

AssetDetail – One-to-one extension of Asset for vendor and warranty information.

2️⃣ maintenance

Handles maintenance request management.

Model:

MaintenanceRequest – Linked to an asset with status and priority tracking.

🔗 Model Relationships

One Building → Many Rooms

One Room → Many Assets

One Asset → One AssetDetail

One Asset → Many Maintenance Requests

All relationships are implemented using Django’s ForeignKey and OneToOneField.

🔄 Maintenance Request Operations

The system allows:

Creating maintenance requests

Viewing and filtering requests

Updating status and priority

Deleting requests (only when status is Pending)

Resolved requests cannot be edited again.

📊 Django ORM Usage

The project uses Django ORM methods such as:

filter()

exclude()

annotate()

Count()

Q() objects

These are used to retrieve:

Non-operational assets

Maintenance count per asset

High-priority unresolved requests

Requests grouped by status

⚙️ Admin Panel

All models are registered in Django Admin with:

Meaningful list display columns

Filters for status and priority

Search functionality using asset name and room number
