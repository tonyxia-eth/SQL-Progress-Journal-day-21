# SQL-Progress-Journal-day-21

# 📊 SQL Learning Journey – Day 21

## 🧠 Focus Area
Continued mastery of Task 7 from the Moneyball project with an emphasis on:
- Multi-table `JOIN`s
- Aggregate functions like `SUM()` and `AVG()`
- `GROUP BY` and `HAVING` filtering
- Introduction to subqueries within `HAVING` clauses

---

## ✅ What I Practiced

### 1. Multi-Table Joins with Aggregates
```sql
SELECT teams.name, SUM(salaries.salary) AS "total salary"
FROM teams
JOIN salaries ON teams.id = salaries.team_id
WHERE salaries.year = 2001
GROUP BY teams.name
ORDER BY "total salary" DESC
LIMIT 5;

✅ Learned how to combine tables using matching keys and calculate total salaries.


SELECT teams.name, ROUND(AVG(salaries.salary), 2) AS "average salary"
FROM teams
JOIN salaries ON teams.id = salaries.team_id
WHERE salaries.year IN (1999, 2000, 2001)
GROUP BY teams.name
HAVING AVG(salaries.salary) > 6000000;

✅ Used HAVING to filter by a condition on an aggregate.

SELECT teams.name, SUM(salaries.salary) AS "total salary"
FROM teams
JOIN salaries ON teams.id = salaries.team_id
GROUP BY teams.name
HAVING SUM(salaries.salary) > (
    SELECT AVG(salary) FROM salaries WHERE year = 2001
);


✅ Compared each team’s total salary to the average using a subquery.

💬 Rule of Thumb Recap
Use GROUP BY when using aggregate functions.

Use HAVING to filter results after aggregation.

Subqueries are useful when your comparison depends on another calculated value.

🏷️ Badge Unlocked

📅 Next Steps
Complete final variations of Task 7

Begin prepping for Task 8: Performance metrics + salary relationships
