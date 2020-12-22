# Introduction
A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

# Project Description
In this project, we model the data with Postgres and build an ETL pipeline using Python. We define fact and dimension tables for a star schema for a particular analytic focus, and write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL.

# Schema
* Fact table
    1. __songplays__ - records in log data associated with song plays i.e. records with page `NextSong`
        * _songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent_
* Dimension tables
    1. __users__ - users in the app
        * _user_id, first_name, last_name, gender, level_
    2. __songs__ - songs in the music db
        * _song_id, title, artist_id, year, duration_
    3. __artists__ - artists in the music db
        * _artist_id, name, location, latitude, longitude_
    4. __time__ - timestamps of records in **songplays** broken down into specific units
        * _start_time, hour, day, week, month, year, weekday_
        
The database is normalized to increase data integrity and developed having the STAR schema in mind.

# How to run

1. Run `create_tables.py` to create the database and tables. 
2. Run `etl.py` to process the datasets and populate the database.

## Additional files
`sql_queries.py` - Create, drop and insert statements. Functions are imported in `etl.py`
`etl.ipynb` - Prototype notebook for `etl.py`
`test.ipynb` - Testing notebook