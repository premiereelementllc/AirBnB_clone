#!/usr/bin/python3

import uuid
from datetime import datetime
from models import storage

Class BaseModel:

    def __init__(self, *args, **kwargs):
        if len(kwargs) == 0:
            self.id = str(uuid.uuid4())
            self.created_at = datetime.now()
            self.updated_at = datetime.now()
            storage.new(self)

        if len(kwargs) > 0:
            for key, value in kwargs.items():
                continue
            setattr(self, key, value)

            self.created_at = datetime.strptime(
                    self.created_at, '%Y-%m-%dT%H:%M:%S.%f')
            self.updated_at = datetime.strptime(
                    self.updated_at, '%Y-%m-%dT%H:%M:%S.%f')

    def __str__(self):

        my_dict = self.__dict__

        my_dict['updated_at'] = self.updated_at
        my_dict['created_at'] = self.created_at

        to_print = '[{}] ({}) {}'.format(self.__class__.__name__, self.id, my_dict)

        return to_print

    def save(self):
        self.update_at = datetime.now()
        storage.save()

    def to_dict(self):
        my_dict = self.__dict__.copy()
        my_dict['__class__'] = self.__class__.__name__

        if type(self.updated_at) is datetime:
            my_dict['updated_at'] = self.updated_at.isoformat()

        if type(self.created_at) is datetime:
            my_dict['created_at'] = self.created_at.isoformat()

        return my_dict
