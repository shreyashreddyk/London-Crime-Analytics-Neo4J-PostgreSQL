# A Hybrid Graph & Relational Analytics Projecy for London Crime Intelligence

This repository documents a sophisticated, multi-faceted analysis on the complex landscape of crime in London. Transcending the limitations of singular database paradigms, this project uses a **hybrid data architecture**, seamlessly integrating the structured analytical power of **PostgreSQL** with the profound network intelligence of **Neo4j**.

The result is not merely a data store, but a dynamic analytical engine capable of moving from high-level statistical aggregation to granular, relationship-based network discovery, revealing the hidden syndicates and operational patterns that define urban crime.

-----

## The Architectural Blueprint: A Deep Dive into the Data Flow

The platform's innovation lies in its meticulously engineered, multi-stage data pipeline that ensures data integrity, analytical performance, and deep insight generation. This is a classic example of **polyglot persistence**, where a best-of-breed technology is chosen for each distinct data domain.

### **Phase 1: The Relational Foundation & Data Warehouse (PostgreSQL)**

The journey begins in the robust, ACID-compliant world of PostgreSQL, which serves as the system's foundational layer for data integrity and structured analytics.

1.  **Ingestion & Staging**: Raw crime data is first ingested into a dedicated staging table (`Staging_Crimes_In_London`). This crucial first step isolates the raw data, providing a resilient foundation for all subsequent transformations and ensuring the purity of the source of truth.
2.  **Dimensional Modeling**: The staged data is then masterfully transformed into a **Star Schema**, a canonical data warehousing pattern optimized for high-performance Online Analytical Processing (OLAP). This model consists of:
      * A central **`Fact_Crimes`** table, containing the quantitative measures of each criminal event.
      * A supporting **`Dim_Boroughs`** dimension table, providing descriptive, contextual attributes.
      * This elegant design, implemented via the provided `ddl.sql` and `dml.sql` scripts, is the bedrock of all statistical reporting and allows for lightning-fast aggregation queries.

### **Phase 2: Graph Synthesis & Network Intelligence (Neo4j)**

This is where the platform transcends traditional analytics. A bespoke Python orchestration script serves as the intelligent bridge between the relational and graph worlds, transforming structured data into a rich, interconnected knowledge graph.

1.  **ETL Orchestration**: The Python application, leveraging the `psycopg2` and `neo4j` drivers, establishes a live connection to the PostgreSQL data warehouse. It systematically extracts the cleaned, validated crime data for synthesis into the graph domain.
2.  **The Graph Data Model**: The script programmatically constructs a sophisticated graph in Neo4j based on the following model:
      * **Nodes**: Entities are modeled as distinct nodes:
          * `Criminal`: Represents individual actors.
          * `Crime_Group`: Represents organized criminal syndicates.
          * `Crime`: Represents specific criminal events, enriched with properties like type and date.
          * `Borough`: Represents the geographical locations.
      * **Relationships**: The true power is unlocked by modeling the explicit connections between these nodes:
          * `[:COMMITTED_CRIME]`: Connects a `Criminal` to a `Crime`.
          * `[:PART_OF_GROUP]`: Links a `Criminal` to a `Crime_Group`, defining the network structure.
          * `[:HAPPENED_IN]`: Geographically situates a `Crime` within a `Borough`.
3.  **Emergent Insight**: This graph model transforms flat, tabular data into a living network. Using Neo4j's native **Cypher query language**, we can now perform analyses that are computationally prohibitive or impossible in a relational model, such as identifying the most influential criminals (centrality analysis), discovering previously unknown links between crime groups, and mapping the spread of criminal activity.


## Core Competencies & Technical Capabilities

This project is a testament to a deep and practical mastery of advanced data engineering principles and technologies.

  * **Architecting Hybrid Data Ecosystems (Polyglot Persistence)**: Visionary design and implementation of a dual-database solution, leveraging the distinct advantages of SQL and NoSQL to build a system that is greater than the sum of its parts.
  * **Advanced Data Warehousing & Dimensional Modeling (PostgreSQL)**: Expertise in classical data warehousing theory and practice, including the design and implementation of a Star Schema optimized for OLAP. Proficient in crafting complex DDL and DML scripts for schema definition and data population.
  * **Complex Network Analysis & Graph Intelligence (Neo4j & Cypher)**: Mastery of graph data modeling to represent complex, real-world systems. Deep proficiency in the **Cypher** query language to traverse relationships, identify patterns, and extract unparalleled network-based insights.
  * **Bespoke ETL Pipeline Orchestration (Python)**: Development of a robust Python-based ETL engine to manage the intricate flow of data between disparate database systems. Proficient with core data libraries and database drivers (`psycopg2`, `neo4j`).


# Team Members: 
Shreyash Kondakindi                             
Kavya Sridhar                             
Susmit Singh

[Video Link](https://drive.google.com/file/d/1ZF9QO7tnyXrrVU-HLYtKCpzHmV4nDAQE/view?usp=sharing)

