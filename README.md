### Docker File 

# python Images use for api  
```
FROM python:3.9
```
Code Working Directory
``` 
WORKDIR /code
```

```
RUN pip install "poetry ==1.1.12"
```

# Copy All The Dependency 
``` 
COPY pyproject.toml pyproject.toml

COPY poetry.lock poetry.lock

COPY changelog.xml changelog.xml

COPY liquibase.properties liquibase.properties

RUN poetry config virtualenvs.create false \ && poetry install --no-interaction --no-ansi
```

# Copy everything into docker 
```
COPY . .
```

# cmd to run application
```
# CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "80"]
```
