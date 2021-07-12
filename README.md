# FastAPI Celery Test

-[x] Integrate Celery into a FastAPI app and create tasks.
-[x] Containerize FastAPI, Celery, and Redis with Docker.
-[x] Run processes in the background with a separate worker process.
-[x] Save Celery logs to a file.
-[x] Set up Flower to monitor and administer Celery jobs and workers.
-[x] Test a Celery task with both unit and integration tests.

## Run the project
```
docker-compose up -d --build
```

Redirect to:
- http://localhost:8004 for app
- http://localhost:5556/ for flower dashboard

## Trigger a task
Run
```
curl http://localhost:8004/tasks -H "Content-Type: application/json" --data '{"type": 1}'
```
Get the task_id, then call the updated endpoint to view the status, example:
```
curl http://localhost:8004/tasks/f3ae36f1-58b8-4c2b-bf5b-739c80e9d7ff
```

Test
```
docker-compose exec web python -m pytest
```

I conclude that celery can be used to execute repeatable tasks and break up complex, resource-intensive tasks so that computational workload can be distributed across a number of machine to reduce the time completion and the load on the machine handling client requests.